# Number-guesser-game

Code by anmabe06

This is a game in where the program choses a random number based on your difficulty level and points.

This is a step by step guide on how to do it:
  1. Show greeting messages:
     ```
      console.log("WELCOME TO THE NUMBER GUESSER");
      console.log("\nThe game is divided into different difficulties, you will advance in the difficulty level as you gain points. The difficulty level sets the range of the number you are trying to guess:\n   Easy --> 0 - 9\n   Medium --> 10 - 99\n   Hard --> 100 - 999\n   Impossible --> 1000 - 9999");
      console.log("\nLet the fun begin!!");
  
  2. Create game function:
     ```
     function game(){
    
   - Set initial variables:
     ```
     points = 0;
	   repetition = 0;
	   difficultyMultiplier = 10;
     
   - Create random number:
     ```
     function randNum(dm){
        number = Math.floor(Math.random() * dm);
        number = Math.round(number);
        return number
     }

   - Create a play again function:
     ```
     function playAgain(){
       input = prompt("Want to play again?\ny/n\n>>")
       if(input == "y"){
         setup(points);
       }else if(input == "n"){
         end();
       }else{
         console.log("Please, introduce 'y' or 'n'");
         playAgain();
       }
     }

   - Create a setup function to set the difficulty:
     ```
     function setup(points){
       number = randNum(difficultyMultiplier);
       if(points <= 20){
         console.log("\n________________________________");
         console.log("Difficulty: Easy");
         console.log("Points: " + points);
         difficultyMultiplier = 10;
       }else if(points > 20 && points <= 50){
         console.log("\n________________________________");
         console.log("Difficulty: Medium");
         console.log("Points: " + points);
         difficultyMultiplier = 100;
       }else if(points > 50 && points <= 70){
         console.log("\n________________________________");
         console.log("Difficulty: Hard");
         console.log("Points: " + points);
         difficultyMultiplier = 1000;
       }else if(points > 70){
         console.log("\n________________________________");
         console.log("Difficulty: Impossible");
         console.log("Points: " + points);
         difficultyMultiplier = 10000;
       }
       compare(number, difficultyMultiplier);
     }

   - Create a compare function to compare the numbers:
     ```
     function compare(number, df){
       input = prompt("Guess >>")
       if (input == number){
         console.log("\nYou Won!");
         points = points + 10 - repetition;
         repetition = 0;
         playAgain();
       }else{
         console.log("\nWrong");
         repetition = repetition + 1;
         clue(number);
       }
     }

   - Create a function to give clues to the user:
     ```
     function clue(number){
       switch(repetition){
         case 1:
           clueNumber = difficultyMultiplier / 2
           if(number >= clueNumber ){
             console.log("Your number is greater than " + clueNumber);
           }else{
             console.log("Your number is lower than " + clueNumber);
           }
           compare(number);
           break;

         case 15:
           numberArray = number.toString().split("");
           console.log("The last digit of your number is " + numberArray[numberArray.length - 1]);
           compare(number);
           break;

         case 30:
           numberArray = number.toString().split("");
           console.log("The last two digits of your number are " + numberArray[numberArray.length - 2] + numberArray[numberArray.length - 1]);
           compare(number);
           break;

         case 31:
           console.log("No clues left");
           compare(number);
           break;

         default:
           compare(number);
       }
     }

   - Call the function setup:
     ```
     setup(points);
  
  3. Create end function:
     ```
     function end(){
       console.log("\n\nSee you soon,\nThanks for playing!")
     }
  
  4. Call game function:
     ```
     game();
  
