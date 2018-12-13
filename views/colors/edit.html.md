USE PALETTE EDIT AS A REFERENCE

USE PALETTE EDIT AS A REFERENCE
# Palettes Edit Page
 Edit pages render forms to make requests to edit data within our database.
 ### Method: PUT
### Action: "palette/{{pallete_id}}/colors/{{color_id}}?_method=PUT"
### Inputs: input fields for each of the columns in the table except id with their value set after getting it from the db
 ## Other things we want to render:
- the button to submit