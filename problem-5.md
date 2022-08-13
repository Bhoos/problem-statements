# Problem Statement 5
React is fast and efficient, doesn’t mean it does not take time

**Requirements:**
- React js/React Native

**Problem Goal:** 
- Find the React optimization issue in the below code

**Problem Description:**
```
function FormComponent {
 const error = useInputError('name');
  return (
   <View>
      <GetProfileInputForm />
      <button disabled={Boolean(error)}>Continue</button>
   </View>
 );
}
```
How and why can the above code affect UI interaction?