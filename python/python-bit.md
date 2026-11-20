# Bitwise Operations & Binary Data

## Conversions

```python
number_dec = 8
number_bin = 0b1000
number_hex = 0x0008

print(bin(number_dec))  # 0b1000
print(hex(number_dec))  # 0x8
print(int(number_bin))  # 8
print(int(number_hex))  # 8
```

```python
# Second arg is the base
print(int("1000", 2))  # 8
print(int("000f", 16))  # 15
```

## Formatting binary numbers

The `08b` means:

- `b`: binary representation.
- `8`: minimum width of 8 characters.
- Leading zeros are added if necessary.

```python
number = 10

print(format(number, "b"))  # 1010
print(format(number, "08b"))  # 00001010
print(format(number, "016b"))  # 0000000000001010

print(format(157, "x"))  # 9d
print(format(157, "02X"))  # 9D
```

## Bitwise operators

| Operator | Name          |                    Purpose |
| -------- | ------------- | -------------------------: |
| `&`      | `AND`         |        Both bits must be 1 |
| `\|`     | `OR`          | At least one bit must be 1 |
| `^`      | `XOR`         |     Bits must be different |
| `~`      | `NOT`         |               Inverts bits |
| `>>`      | `Right shift` |           Moves bits right |
| `<<`      | `Left shift` |           Moves bits left |

### Bitwise `AND`, `OR`, `XOR`

```python
bitwise_and = 0b0011 & 0b1101  # 0001
bitwise_or = 0b1010 | 0b0101  # 1111
bitwise_xor = 0b1011 ^ 0b0101  # 1110
```

### Bitwise `NOT`

> [!IMPORTANT]
> Python's `~` inverts bits, but the result is interpreted as a **signed integer**, not an automatically fixed-width binary value.

The mathematical relationship is:

$\sim x = -x-1$

```python
x = 12

print(~x)  # -13
```

### Inverting bits

```python
x = 0b1101
y = 0b10101010

invert_x = (~x) & 0xF
invert_y = (~y) & 0xFF

invert_x_xor = x ^ 0xF

print(format(invert_x, "04b"))
# 0010
print(format(invert_y, "08b"))
# 01010101
print(format(invert_x_xor, "04b"))
# 0010
```

### Bitwise `SHIFT`

```python
x = 0b1000

print(format(x >> 1, "04b"))  # 0100
print(format(x >> 3, "04b"))  # 0001
print(format(x << 1, "04b"))  # 10000
```

### The four fundamental bit operations

| Goal | Operation | Formula |
|---|---|---|
| Check bit | AND | `value & mask` |
| Set bit | OR | `value \| mask` |
| Clear bit | AND + NOT | `value & ~mask` |
| Toggle bit | XOR | `value ^ mask` |


### Checking whether a bit is set

Suppose you want to check whether bit position 2 is `1`.

Remember that bit positions start at zero, from the right.

```python
Position:  7 6 5 4 3 2 1 0
Value:     1 0 1 1 0 1 1 0
```

Create a mask that has only bit 2 enabled then `AND` the value and the mask.

```python
value = 0b10110110
mask = 1 << 2  # 0100

result = value & mask

print(result)  # 4
print(result != 0)  # True
```

### Setting a bit

```python
# Set bit 2 to "1"
value = 0b1011
mask = 1 << 2  # 0100
result_1 = value | mask
print(format(result_1, "04b"))  # 1111
```

### Clearing a bit

```python
value = 0b11111111

mask = 1 << 2

value = value & ~mask

print(format(value, "08b"))
# 11111011
```

### Toggling a bit

```python
value = 0b10110110

mask = 1 << 2

value = value ^ mask
print(format(value, "08b"))  # 10110010
value ^= mask
print(format(value, "08b"))  # 10110110
```

## Subnetting example

```
IP address: 192.168.1.10
Subnet:     255.255.255.0 (/24)
```

Convert to binary

```
IP:
11000000.10101000.00000001.00001010

Mask:
11111111.11111111.11111111.00000000
```

Bitwise `AND`

```
IP:       11000000.10101000.00000001.00001010
Mask:     11111111.11111111.11111111.00000000
          -----------------------------------
Result:   11000000.10101000.00000001.00000000

192.168.1.0
```

```python
from ipaddress import ip_address


def ipv4_to_bin(ip_string: str) -> int:
    octets = ip_string.split(".")
    binary = "".join(format(int(octet), "08b") for octet in octets)
    return int(binary, 2)


ip_addr = "192.168.1.10"
subnet = "255.255.255.0"

ip_bin: int = ipv4_to_bin(ip_addr)
subnet_bin: int = ipv4_to_bin(subnet)

network = ip_bin & subnet_bin
print(ip_address(network))  # 192.168.1.0
```

## `bytes`

A built-in type that represents an immutable sequence of integers, where each integer must be between 0 and 255.

`bytes()` converts those integers into bytes.

```python
data = bytes([65, 66, 67])
# those values correspond to ASCII characters

print(data)  # b'ABC'

print(data[0])  # 65
print(data[1])  # 66
print(data[2])  # 67
```

## `bytearray`

Mutable sequence of bytes

```python
data = bytearray([65, 66, 67])

print(data)  # bytearray(b'ABC')

data[0] = 70

print(data)  # bytearray(b'FBC')
```

`bytearray(data)` creates a new, independent object. It is not a shallow copy or a reference to the original object.

```python
data = bytes([65, 66, 67])
# b'ABC'

editable = bytearray(data)
editable[0] = 70
print(editable)
# bytearray(b'FBC')

result = bytes(editable)
# b'FBC'
```

```python
for byte in bytearray(b"ABC"):
    print(byte)

# 65
# 66
# 67

for byte in bytes([65, 66, 67]):
    print(byte)

# 65
# 66
# 67
```

## Creating empty or zero-filled bytes

- `bytes()` creates an empty sequence.
- `bytes(4)` creates a sequence containing four zero bytes.

```python
a = bytes()
b = bytes(4)

print(a)  # b''
print(b)  # b'\x00\x00\x00\x00'
```

## `bytes.fromhex()`

- `data1[0]` uses indexing. It returns one integer representing the byte at index 0.
- `data2[0:2]` uses slicing. It returns a new bytes object containing bytes at indices 0 and 1.

```python
data1 = bytes.fromhex("41 42 43")
print(data1)  # b'ABC'

data2 = bytes.fromhex("414243")
print(data2)  # b'ABC'

print(data1[0])  # 65
print(data2[0:2])  # b'AB'
```

## Converting integers to bytes

Imagine you have this integer:

`number = 1000`

You know that its binary representation is:

`1111101000` or `0b1111101000`

What if you want to store that integer in a binary file or send it over a network?

You need to decide how many bytes to use and how to arrange them.

### `int.to_bytes(length, byteorder, signed)`

1. `length` - represent the integer using exactly `x` bytes
2. `byteorder` - store the most significant byte first

Big-endian byte order:

`03` - Most significant
`E8` - Least significant

```python
number = 1000

data = number.to_bytes(2, byteorder="big")

print(data)  # b'\x03\xe8'
print(data.hex())  # 03e8

print(bin(number) == bin(0x03E8))  # True
```

Little-endian byte order:

```python
number = 1000

data = number.to_bytes(2, byteorder="little")
data2 = number.to_bytes(2, byteorder="big")


print(data)  # b'\xe8\x03'
print(data.hex())  # e803

print(data2)  # b'\x03\xe8'
print(data2.hex())  # 03e8
```

## Convert from `bytes` to `int`

```python
data = bytes.fromhex("00 01")

number_big = int.from_bytes(data, byteorder="big")
number_little = int.from_bytes(data, byteorder="little")

print(number_big)  # 1
print(number_little)  # 256
```

## Overflow Error

1 byte is not enough to represent `1000`

```python
number = 1000

big = number.to_bytes(1, byteorder="big")
# OverflowError: int too big to convert

big = number.to_bytes(1, byteorder="little")
# OverflowError: int too big to convert
```

## Signed integers

Python integers **don't** have a fixed width.

Instead, Python behaves as if negative integers have infinitely many leading 1 bits when performing bitwise operations.

```python
neg_signed = (-100).to_bytes(2, "big", signed=True)
pos_signed = (+100).to_bytes(2, "big", signed=True)
pos_num = (100).to_bytes(2, "big", signed=True)

print(neg_signed)  # b'\xff\x9c'
print(pos_signed)  # b'\x00d'
print(pos_num)  # b'\x00d'

neg_num = int.from_bytes(neg_signed, "big", signed=True)
neg_num2 = int.from_bytes(neg_signed, "big", signed=False)

print(neg_num)  # -100
print(neg_num2)  # 65436

neg_num_s_false = (-100).to_bytes(2, "big", signed=False)
# OverflowError: can't convert negative int to unsigned
```

## Encoding and decoding

Computers often need to transmit or store text as bytes.

Character encoding:

- An encoding defines how characters are represented as bytes.

Python provides two particularly important methods:
- `.encode()` — string to bytes.
- `.decode()` — bytes to string.

### ASCII

```python
text = "ABC"

data = text.encode("ascii")

print(data)  # b'ABC'
print(data.hex())  # 414243
```

### UTF-8

```python
text = "Café"

data = text.encode("utf-8")

print(data)  # b'Caf\xc3\xa9'
print(data.hex())  # 436166c3a9

cafe_hex = bytes.fromhex("43 61 66 C3 A9")
cafe_text = cafe_hex.decode("utf-8")
print(cafe_text)  # Café
```

## Reading and writing hexadecimal bytes

### Convert bytes to hexadecimal

```python
data = bytes([72, 101, 108, 108, 111])

print(data.hex())  # 48656c6c6f

print(data.hex(" "))  # 48 65 6c 6c 6f
```

### Convert hexadecimal into bytes

```python
data = bytes.fromhex("48 65 6c 6c 6f")

print(data)  # b'Hello'
```

### Change individual bytes using hexadecimal

```python
data = bytearray.fromhex("48 65 6c 6c 6f")

data[0] = 0x4A

print(data.hex(" "))  # 4a 65 6c 6c 6f

print(data)  # bytearray(b'Jello')
```

### Hexadecimal as a debugging tool

You might eventually encounter something like this when inspecting a file or network packet:

```
0000   45 00 00 3C 1C 46 40 00
0008   40 06 B1 E6 C0 A8 01 01
0010   C0 A8 01 02
```

This is a **hexadecimal dump**.

Each pair represents one byte. The left column indicates the offset (position) in the data.

**Try it out**

1. Copy the below into a `txt` file.

```
Hello how are you?
I am ABC
abc
def
```

2. Run `xxd <name>.txt`

```
00000000: 4865 6c6c 6f20 686f 7720 6172 6520 796f  Hello how are yo
00000010: 753f 0a49 2061 6d20 4142 430a 6162 630a  u?.I am ABC.abc.
00000020: 6465 660a                                def.
```

## Integer Methods

### `bit_length()`

`bit_length()` tells you how many bits are needed to represent an integer in binary, excluding the sign and leading zeros.

```python
x = 10
y = -10

print(bin(x))  # 0b1010
print(x.bit_length())  # 4

print(bin(y))  # -0b1010
print(y.bit_length())  # 4
```

### `bit_count()`

`bit_count()` counts how many 1 bits appear in the binary representation of the integer's absolute value.

```python
x = 13

print(bin(x))  # 0b1101
print(x.bit_count())  # 3
```

### `to_bytes()`

This method converts an integer into a sequence of bytes.

```python
number = 1000

data = number.to_bytes(2, byteorder="big")

print(data)  # b'\x03\xe8'
print(data.hex())  # 03e8
```

### `from_bytes()`

It converts bytes back into an integer.

```python
data = bytes.fromhex("03 E8")
number = int.from_bytes(data, byteorder="big")
print(number)  # 1000

data = bytes.fromhex("FB")
number = int.from_bytes(data, "big", signed=True)
print(number)  # -5
```

### `int.as_integer_ratio()`

This method expresses an integer as a fraction consisting of a numerator and denominator.

The return value is a `tuple` containing two integers.

Every integer can be expressed as `x = x/1`

```python
print((10).as_integer_ratio())  # (10, 1)
print((-5).as_integer_ratio())  # (-5, 1)
print((0).as_integer_ratio())  # (0, 1)
```

```python
x = 0.5
y = 0.75
z = 9.5

print(x.as_integer_ratio())
# (1, 2)

print(y.as_integer_ratio())
# (3, 4)

print(z.as_integer_ratio())
# (19, 2)
```

## `struct` module

The struct module lets you convert Python values into binary data structures and back again.

| Symbol | Meaning |
|:---:|---|
| `>` | Big-endian |
| `<` | Little-endian |
| `H` | Unsigned 16-bit integer |
| `h` | Signed 16-bit integer |
| `I` | Unsigned 32-bit integer |
| `i` | Signed 32-bit integer |
| `B` | Unsigned 8-bit integer |
| `b` | Signed 8-bit integer |
| `f` | 32-bit float |
| `d` | 64-bit float |

### Pack

```python
import struct

data = struct.pack(">H", 1000)

print(data)  # b'\x03\xe8'
print(data.hex())  # 03e8
```

### Unpack

```python
import struct

data = bytes.fromhex("03 E8")

result = struct.unpack(">H", data)

print(result)  # (1000,)
```

### (Un)packing multiple values

```python
import struct

# 255 as an unsigned 8-bit integer.
# 1000 as an unsigned 16-bit integer.
data = struct.pack(">B H", 255, 1000)

print(struct.unpack(">BH", data))
# (255, 1000)
```

### Why `struct` is useful

Imagine creating a binary file format with this structure:

| Field | Type | Size |
|---|---|---:|
| File version | Unsigned 8-bit | 1 byte |
| File size | Unsigned 32-bit | 4 bytes |
| Temperature | 32-bit float | 4 bytes |

```python
import struct

# encode the entire header
header = struct.pack(">BIf", 1, 1024, 23.5)

# read it back
version, size, temperature = struct.unpack(">BIf", header)

print(version)  # 1
print(size)  # 1024
print(temperature)  # 23.5
```
