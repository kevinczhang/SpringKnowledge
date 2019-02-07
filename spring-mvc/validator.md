# Validator

[JSR 303](http://jcp.org/en/jsr/detail?id=303) \(Bean Validation\) is the specification of the Java API for JavaBean validation in Java EE and Java SE. Simply put it provides an easy way of ensuring that the properties of your JavaBean\(s\) have the right values in them. Examples:  @Size\(min=2, max=30\), @NotNull @Min\(18\) @Max\(100\),  @Past

@NotEmpty and @DateTimeFormat annotations that are additional to JSR-303 and provided by hibernate validator implementation. 

#### Custom Validator Implementations

```java
package com.journaldev.spring.form.validator;

import javax.validation.ConstraintValidator;
import javax.validation.ConstraintValidatorContext;

public class PhoneValidator implements ConstraintValidator<Phone, String> {

	@Override
	public void initialize(Phone paramA) {
	}

	@Override
	public boolean isValid(String phoneNo, ConstraintValidatorContext ctx) {
		if(phoneNo == null){
			return false;
		}
		//validate phone numbers of format "1234567890"
        if (phoneNo.matches("\\d{10}")) return true;
        //validating phone number with -, . or spaces
        else if(phoneNo.matches("\\d{3}[-\\.\\s]\\d{3}[-\\.\\s]\\d{4}")) return true;
        //validating phone number with extension length from 3 to 5
        else if(phoneNo.matches("\\d{3}-\\d{3}-\\d{4}\\s(x|(ext))\\d{3,5}")) return true;
        //validating phone number where area code is in braces ()
        else if(phoneNo.matches("\\(\\d{3}\\)-\\d{3}-\\d{4}")) return true;
        //return false if nothing matches the input
        else return false;
	}

}
```



