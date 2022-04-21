# Base64

# 1. 개요
### 1) 인코딩
- 1. 8비트 3개를 6비트 4개로 쪼갠다.
- 2. 6비트를 정수값으로 변경한다.
- 3. 정수값을 base64 테이블을 통해 변환한다.

### 2) 디코딩
- 1. 정수를 8비트 바이너리 리스트로 변경한다.
- 2. 24개씩 잘라서 아스키 문자열로 변경한다.

# 2. 코드
```python
class Base64:

    def __init__(self):
        self.table = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/"
        self.ascii_dict = {}
        for idx, val in enumerate(self.table):
            self.ascii_dict[val] = idx

    def encode(self, s: str):

        binary_list = self.__str_to_binary_list(s)

        binary_str = "".join(binary_list)

        hex_list = self.__binary_str_to_binary_list(binary_str, 6)

        res = "".join(self.__hex_list_to_ascii_list__(hex_list))

        return self.__fill_encoded_empty(res)

    def decode(self, s):

        s = s.replace("=", "")

        int_list = self.__int_list_from_str(s)

        binary_list = self.__int_list_to_binary_list(int_list)

        octa_list = self.__binary_str_to_binary_list("".join(binary_list), 8)

        order_list = self.__octa_list_to_order_list(octa_list)

        return "".join(self.__order_list_to_ascii_list(order_list))

    def __order_list_to_ascii_list(self, order_list):
        return [chr(x) for x in order_list if x != 0]

    def __octa_list_to_order_list(self, octa_list):
        return [self.__binary_to_int(x) for x in octa_list]

    def __int_list_to_binary_list(self, int_list):
        return [self.__int_to_binary__(x, 6) for x in int_list]

    def __int_list_from_str(self, s):
        return [self.ascii_dict[x] for x in s]

    def __fill_encoded_empty(self, s):
        diff = len(s) % 4
        return s + "=" * (4 - diff) if diff != 0 else s

    def __binary_str_to_binary_list(self, binary_str, base):
        hex_list = []
        for i in range(0, len(binary_str), base):
            hex_list.append(format(binary_str[i:i+base]).ljust(base, '0'))
        return hex_list

    def __hex_list_to_ascii_list__(self, hex_list):
        return [self.table[self.__binary_to_int(hx)] for hx in hex_list]

    def __str_to_binary_list(self, s: str):
        return [self.__int_to_binary__(ord(c), 8) for c in s]

    def __int_to_binary__(self, n:int, base: int):
        return "{0:b}".format(n).zfill(base)

    def __binary_to_int(self, b):
        return int(b, 2)
```