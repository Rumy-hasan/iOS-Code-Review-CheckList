# iOS-Code-Review-CheckList
I am adding this list with the collection of different source.
Some are:
- https://gist.github.com/pallavtrivedi03/8f4975a41f5b64d8a6af4fd119949d39
- https://dev.to/bornfightcompany/ios-code-review-checklist-53ia
- https://medium.com/swiftcairo/ios-code-review-checklist-482f17f5c7c6

## General:
  ### Avoid Type Inference: If you know the actual type the write it done because type inference increase compiler time. To Usderstand properly, please read [this](https://stackoverflow.com/questions/37707403/what-is-the-difference-between-type-safety-and-type-inference) 
  
  ### Prefer using Higher Order Functions: If possible use Higher Order Functions as they are more optimal. Increase the code quality.
  
  ### force unwraps: Make sure that there are no force unwraps
  
  ### retain cycles: Make sure that there are no retain cycles
  
  ### deprecated API: Check if any deprecated API is being used
  
  ### Check for magic numbers and use enum: Avoid harcoding, avoid magic numbers, if needed extract into a constant. If added, magic numbers should be commented. Better to use enum.
  
  ### Use native API: Check if there’s any API provided by Apple which can make things simple. 
  
  ### Try to avoid nested structures as much as possible. (loops, if/else)
  
  ### Index Out Of Bound Exception: Wherever accessing the values from an Array is involved, check if there’s any possibility of Index Out Of Bound Exception.
  
  ### Check if there are any unintended changes in the code.
  
  ### Check for the corner cases. Example -  Error Handling (what if the backend doesn’t send an error message).
  
  ### If there’s any complex logic involved, check if there’s a comment to explain it. 
  
  ### Do proper Indentations.
  
  ### Fonts, Colors etc shouldn’t be accessed randomly. There should be a separate file for them. 
  
  ### Make sure that the directory structure is being followed.
  
  ### See if the guidelines set by the team is being followed - SwiftLint (I also not use it. Need to learn.)
  
  ### Test Cases(if we write) - Code Coverage of the new code. Also see that the code is written for isolate test.
  
  

