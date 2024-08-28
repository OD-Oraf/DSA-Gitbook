# Arrays

## Ram

Arrays are a contiguous(no space in between) block of data stored in RAM. Every piece of information has a value and its address.

## Bit storage in RAM

Integers are represented as 4 bytes, or 32 bits. When entered in RAM, the address increases by 4 bytes to represent each integer. Characters are represented with one byte so the addressing will increment by 1

## Static Arrays

Static array are those of fixed size.&#x20;

### Array operations

<table><thead><tr><th width="280.5">Operation </th><th>Big O TIme</th></tr></thead><tbody><tr><td>Read/Write i-th element</td><td>O(1)</td></tr><tr><td>Insert/Remove End</td><td>O(1)</td></tr><tr><td>Insert Middle</td><td>O(n) - need to move elements over to allow space</td></tr><tr><td>Remove Middle</td><td>O(n)</td></tr></tbody></table>

## Stack

LIFO - Last in First Out data structure

| Operation  | Big-O time |
| ---------- | ---------- |
| Push       | O(1)       |
| Pop        | O(1)       |
| Peek/Top   | O(1)       |

