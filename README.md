# Batched Yield-Safe Signal Implementation with a call function, allowing for the returning of values
## Main changes
- Added a :Call method which acts similarly to :Fire except it yields for results and returns a table of them. {[key or number] = results}
- When connecting to a signal, you can now provide a key as the second parameter which the results will be stored under if call is used. Here's an example:
```lua
local NewSignal = Signal.new()
NewSignal:Connect(function(a, b)
  return a + b
end, "Addition")

local Results = NewSignal:Call(1, 1)
local AdditionResult = table.unpack(Results["Addition"]) --> 2
```
## Others
- Added some basic typing, not used very well but it's a start.
- Added a :WaitFor method which yields to wait for the signal to be fired with parameters that match a condition set by the function provided.
