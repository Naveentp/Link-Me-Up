# Basics
Unlike including all the concepts of iOS, this is just a TIL [Today I Learned] list.

### Swift Basics


- **Dictionaries with default values**
	```
	let address = ["city": "Bangalore", "state": "Karnataka"]
	address["city"] // Prints Bangalore
	address["Country"] // nil
	address["Country", default: "Unknown"] // prints Unknown
	```


- **Tuples**
 	```
 	var name = (first: "Naveen", last: "T P")
 	name.0 //prints Naveen
 	name.first //print Naveen
 	```


 - **`fallthrough` keyword in switch statement**  
 	If you want execution to continue on to the next case, use `fallthrough`
 	```
 	switch arithmatic {
		case "plus":
    		print("addition")
		case "minus":
    		print("substraction")
		case "star":
    		print("Multiply")
    		fallthrough
		default:
    		print("None")
	}
 	```


- **`inout` keyword in function parameter**  
	Parameters passed to functions are constants. If you want to change the variable inside function use `inout` keyword in the parameter.  
	**Note**: variable should be created using `var` and use `&` while passing the parameter in the function

	```
	func greet(name: inout String) {
    	name += "Naveen"
	}

	var greetMessage = "Hey " 
	greet(name: &greetMessage) //prints Hey Naveen
	```


- **Closures**
	- Default
	```
	let welcomeGuest = {
    	print("Welcome Guest")
	}

	welcomeGuest() //prints Welcome Guest
	```
	- Parameterised with return value
	```
	let welcomeUser = { (name : String) -> String in
   		return "Welcome \(name)"
	}

	let result = welcomeUser("Naveen") //result is Welcome Naveen
	```


- **Using closure as parameter [Similar to Higher order functions in kotlin]**
	```
	let downloadingImg = {
        print("downloading...")
	}

	func dowloadImage(action: () -> Void){
    	print("Download started")
    	action()
    	print("Downlaoad ended")
	}

	//Usage
	
	dowloadImage(action: downloadingImg)

	//or

	dowloadImage {
		print("downloading...")
	}
	```






















