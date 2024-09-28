---
title: Programming Task - Improving the Bubble Sort
---

# {{ title }}

1. Make the improvements to the Bubble Sort routine as mentioned in the text previously
2. Create a top films program that stores your top 5 films in an array. Use this code to start: `string[] films = { "ADD", "YOUR", "TOP", "5", "FILMS" };` The program should:
      - Create a string array with your top 5 films (use the template code above)
      - Display each of the films using a foreach loop
      - Sort the array into ascending order using Array.Sort() then display the elements
      - Reverse the array into descending order using Array.Reverse() then display the elements
      - Replace the last film from the reversed array with another film then display the elements

3. Create a subject entry program that allows a user to input all the subjects they are studying and then displays the list of subjects back to them. The program should:
    - Ask the user for the number of subjects they currently study
    - Create an array with a length that matches the number of subjects
    - Use a loop to store each subject as an element in the array
    - Use another loop to output all the subjects entered
    - __Challenge__: Allow the user to modify their subject choices.

## Extension Activity

You have been asked to create a cinema seating program for a local cinema. The cinema needs to keep track of which seats are filled and which are empty. The screens all have 10 rows of seats (A-J) and 18 seats per row. If a seat is booked, it should record whether it is an adult or child sat there.

Your program should:

- Use a 2D array to represent the seating for a screen
- Display all of the seats to see which ones are booked or empty
- Allow the user to book a specific seat if the seat is empty
- Allow the user to book multiple seats next to each other in a row
- Output the total number of adult seats booked, child seats booked, and seats left
