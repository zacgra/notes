initialize a hash of arrays
`hash = Hash.new {|h, k| h[k] = Array.new}`

```rb
def char_indices(str)
    hash = Hash.new {|h, k| h[k] = Array.new}
    str.each_char.with_index do |char, i|
      hash[char] << i
    end
    hash
end
```
