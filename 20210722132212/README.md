 # Figured out what noremap means.

 In vim all mappings are recursive. If you map `y` to `h` using `nmap` for normal mode mapping. Each time you press `y` it will map to `h` and move you. However if you have a mapping that also maps `h` to something else like `e`, everytime you press `y` or `h` it will actually press `e`. This is where noremap comes in. It will stop vim from running the other remappings. So if we do `noremap y h` `y` will remap to `h` but if we had previously used a mapping it wont remap `y` to that mapping.
