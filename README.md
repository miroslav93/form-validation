# Vanilla JavaScript form validation
Vanilla JavaScript template for form validation with regular expressions

These two files contain the barebone template for form validation using JavaScript regular expressions, if HTML5 validation is not available for whatever reason (or even if it is, as regular expressions are far more powerful tools for this purpose).

The template already has name, zipcode, email address and phone number.

The name accepts any character string between 2 and 20 characters. Only a single name is required here.

The zipcode and phone number fields are in the US format.
The zipcode accepts input in the following format:
 - nnnnn-ooo
n = number
o = optional number
the dash is optional as well

the email address field accepts the following format
(any number of alphanumerical symbols)@(any number of alphanumerical symbols).(up to five characters)
Example johndoe123@test1test1test.media

The phone number accepts the following formats
 - nnn-nnn-nnnn
 - (nnn)-nnn-nnnn
 - nnnnnnnnnn
n = number

# Modifying validations
In order to make modifications to the existing validators, you will have to go into the app.js file and modify the regular expressions in the following manner

Name validation:
const re = /^[a-zA-z]{2,20}$/;
will have to be modified to:
const re = /^[a-zA-z]{MINIMUM NUMBER OF CHARACTERS HERE,MAXIMUM NUMBER OF CHARACTERS HERE}$/;
an if you would like to have numbers viable within the name, for whatever reason:
const re = /^[a-zA-z0-9]{MINIMUM NUMBER OF CHARACTERS HERE,MAXIMUM NUMBER OF CHARACTERS HERE}$/;

Zipcode validation
const re = /^[0-9]{5}(-[0-9]{4})?$/;
will have to be modified to:
const re = /^[MIN NUMBER-MAX NUMBER]{TOTAL AMOUNT OF NUMBERS}$/;
the remaining part, which is (-[0-9]{4})? is optional and can be added depending on your regional zipcode format

Email validation
const re = /^([a-zA-Z0-9_\-\.]+)@([a-zA-Z0-9_\-\.]+)\.([a-zA-Z]{2,5})$/;
will have to be modified to
const re = /^([a-zA-Z0-9_\-\.]+)@([a-zA-Z0-9_\-\.]+)\.([a-zA-Z]{MIN NUMBER,MAX NUMBER})$/;

Phone validation
const re = /^\(?\d{3}\)?[-. ]?\d{3}[-. ]?\d{4}$/;
will have to be modified to
const re = /^\(?\d{NUMBER OF ALLOWED NUMBERS FOR THE FIRST PART}\)?[-. ]?\d{NUMBER OF ALLOWED NUMBERS FOR THE SECOND PART}[-. ]?\d{NUMBER OF ALLOWED NUMBERS FOR THE THIRD PART}$/;

For any larger modifications, familiarity with JavaScript regular expressions might be needed.
