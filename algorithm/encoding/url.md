# url encoding

```python
class urlparser:
    def __init__(self):
        # 예약되지 않은 문자
        self.UNRESERVED_TEXT_SET = set("ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789-_.~")
        # 예약된 문자
        self.RESERVED_TEXT_SET = set("!*'();:@&=+$,/?#[]")

    def encode(self, url: str, is_reserved_text_encode: bool) -> str:
        encoded = []

        for char in url:
            # 1) 아스키 문자이고, 예약되지 않은 문자는 그대로 넣습니다.
            if char in self.UNRESERVED_TEXT_SET:
                encoded.append(char)
            # 2) 아스키 문자이고, 예약된 문자는 16진수로 넣습니다.
            elif char in self.RESERVED_TEXT_SET:
                # 예약된 문자도 모두 인코딩 하는 경우
                if is_reserved_text_encode:
                    encoded.append("%{:02X}".format(ord(char)))
                # 예약된 문자를 인코딩 하지 않는 겨웅 그대로 넣습니다.
                else:
                    encoded.append(char)
            # 3) 아스키가 문자가 아니면, UTF-8로 인코딩후 2자리씩 끊어서 대문자로 넣습니다.
            else:
                encoded_str = char.encode('utf-8').hex()
                for i in range(0, len(encoded_str), 2):
                    encoded.append(f"%{encoded_str[i:i + 2].upper()}")

        return "".join(encoded)

    def decode(self, url: str) -> str:
        decoded = []

        # 1) %로 시작하는 문자열을 찾습니다.
        i = 0
        while i < len(url):
            if url[i] == '%':
                hex_str = url[i + 1:i + 3]
                decoded_str = chr(int(hex_str, 16))
                # 1) 아스키 문자이고, 예약된 문자인 경우
                if decoded_str in self.RESERVED_TEXT_SET:
                    decoded.append(decoded_str)
                    i += 3
                # 2) 아스키가 아닌 문자인 경우 3바이트 끊어서 디코딩합니다.
                else:
                    hex_str = url[i:i + 9].replace("%", "")
                    decoded_str = bytes.fromhex(hex_str).decode('utf-8')
                    decoded.append(decoded_str)
                    i += 9
            # 3) 아스키 문자이고, 예약되지 않은 문자는 그대로 넣습니다.
            else:
                decoded.append(url[i])
                i += 1

        return "".join(decoded)


url_parser = urlparser()

original_url = "https://velog.io/@skyepodium/URL-인코딩-알아보기-feat.-파이썬-구현"
print('원래 url:', original_url)
# 원래 url: https://velog.io/@skyepodium/URL-인코딩-알아보기-feat.-파이썬-구현

print()

# 1) 예약된 문자열 인코딩하는 경우
encoded_url = url_parser.encode(original_url, True)
print('1) 예약된 문자열 인코딩하는 경우: ', encoded_url)
# 인코딩 url: https%3A%2F%2Fvelog.io%2F%40skyepodium%2FURL-%EC%9D%B8%EC%BD%94%EB%94%A9-%EC%95%8C%EC%95%84%EB%B3%B4%EA%B8%B0-feat.-%ED%8C%8C%EC%9D%B4%EC%8D%AC-%EA%B5%AC%ED%98%84

decoded_url = url_parser.decode(encoded_url)
print('디코딩 url:', decoded_url)
# 디코딩 url: https://velog.io/@skyepodium/URL-인코딩-알아보기-feat.-파이썬-구현

print()

# 2) 예약된 문자열은 인코딩 하지 않는 경우
encoded_url = url_parser.encode(original_url, False)
print('2) 예약된 문자열은 인코딩 하지 않는 경우: ', encoded_url)
# 인코딩 url: https%3A%2F%2Fvelog.io%2F%40skyepodium%2FURL-%EC%9D%B8%EC%BD%94%EB%94%A9-%EC%95%8C%EC%95%84%EB%B3%B4%EA%B8%B0-feat.-%ED%8C%8C%EC%9D%B4%EC%8D%AC-%EA%B5%AC%ED%98%84

decoded_url = url_parser.decode(encoded_url)
print('디코딩 url:', decoded_url)
# 디코딩 url: https://velog.io/@skyepodium/URL-인코딩-알아보기-feat.-파이썬-구현
```