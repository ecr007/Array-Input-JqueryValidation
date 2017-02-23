# Array Input JqueryValidation
Permitir la validación de todos los campos array

# Primero Validamos los campos

```
  $("#signupForm").validate({
        rules: {
            "category[]": "required"
        },
        messages: {
            "category[]": "Please select category",
        }
  });
```

# Editamos la funcion checkForm del jqueryValidation

```

checkForm: function() {
    this.prepareForm();
    for (var i = 0, elements = (this.currentElements = this.elements()); elements[i]; i++) {
        if (this.findByName(elements[i].name).length != undefined && this.findByName(elements[i].name).length > 1) {
            for (var cnt = 0; cnt < this.findByName(elements[i].name).length; cnt++) {
                this.check(this.findByName(elements[i].name)[cnt]);
            }
        } else {
            this.check(elements[i]);
        }
    }
    return this.valid();
}

```
