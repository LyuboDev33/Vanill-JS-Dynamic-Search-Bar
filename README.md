This is a dynamic search bar created with Vanilla JavaScript, HTML and CSS using 'keyup' to dynamically find users. 

Notes: 
1. Project is not responsive
2. JavaScript code is located inside index.html since the project is small

How it works:

1. We fetch data from a test API website: https://jsonplaceholder.typicode.com/users and store the results in a variable

 fetch('https://jsonplaceholder.typicode.com/users')
      .then(function (response) {
        return response.json();
      })
      .then(function (json) {

        let getData = json;

!!! getData returns an array with Objects with users information inside every object. !!!

2. The info from the API is used to dynamically add the users on the screen

We take the value from the input field and use toLowerCase() to avoid case sensitivity later on.

let inputField = document.getElementById('nameSeach');
let searchValue = inputField.value.trim().toLowerCase();

We loop though the getData array and take the values (the name and email) from each object and store them in variables.

containerUsers.innerHTML = ''; (This line of code removes all the users before dynamically adding the ones that match the below if statement)

 for (let i = 0; i < getData.length; i++) {
        
            let user = getData[i];

            let userName = user.name.toLowerCase();
            let userEmail = user.email.toLowerCase();

            if (userName.includes(searchValue) || userEmail.includes(searchValue)) {
              containerUsers.insertAdjacentHTML('beforeend',
                `<div class="users">
                  <p class="names">${user.name}</p> 
                <p class="email">${user.email}</p> 
                <p class="phone">${user.phone}</p> 
                </div>`
              );
            }
          }
        }

Note: We use toLowerCase() for both variables again to avoid case sensitivity.

Before we add all the users to the page dynamically, we create an if statement to check if the input field value matches the value of the name or email. 

In simpler words - 
First: We get the value from the input field. 
Second: We get the values from the name and email
Third: We check with includes() if the value from the input matches with the email or names.

If yes - we display those users dynamically: 

if (userName.includes(searchValue) || userEmail.includes(searchValue)) {
              containerUsers.insertAdjacentHTML('beforeend',
                `<div class="users">
                  <p class="names">${user.name}</p> 
                <p class="email">${user.email}</p> 
                <p class="phone">${user.phone}</p> 
                </div>`
              );
            }
            
If input field is empty, it will return all of the results dynamically anyways.
Once you start writing, it will begin to filter the users based on keywords you wrote. 

Project can be downloaded and used freely if you need it :) 

