# Make Your Own Computer Game
This project is to make a computer game with Unity. The game can be anything and in the cases of this project, I am making a 2d game called Pacman Isle which is a platformer game just like Super Mario Bros.  

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Arnesh K | Irvington High School | Software Engineering | Incoming Senior

<iframe mozallowfullscreen="true" allow="autoplay; fullscreen" src="https://arneshkumar.github.io/arneshbluestamp/PacmanGame/index.html" style="border:0px #000000 none;" name="My Game" scrolling="no" msallowfullscreen="true" allowfullscreen="true" webkitallowfullscreen="true" allowtransparency="true" frameborder="0" marginheight="px" marginwidth="320px" height="500px" width="700px"></iframe>

# Demo Night

Here is the Demo Night for my project, which is the Make Your Own Computer Game!



# Character Moving Left, Right, and Jumping

My second milestone was getting my character to move left, right, and jump where I had to make the C# script. I added the Rigidbody2D component to Pacman in order to allow it to react to real time physics, which is, in this case, gravity. I added a circle collider 2D to Pacman and box collider 2d to the ground so that there can be collision detected between the character and ground, and so that the character jumps and does not fall right below the ground. I then had to write the C# script to get my character moving left, right, and jumping. The main way I wanted my character to move was to flip the Pacman when switching to different directions (either left or right). After writing the C# script, my character was moving slowly and rotating, so in order to fix that problem, I had to talk with my instructor and I was able to figure out how to stop the rotation and make my character move faster. I also had to use the Animator tab to create the idle animation (Pacman closed mouth) and the moving animation (Pacman closed mouth and open mouth). In my C# script, I had to also talk with my instructor in order to figure out how to play the animation states depending on if my character is moving or not. In addition, after getting my character to move left, right, and jump, I also had to figure out when my character should be able to jump which is when the character is on the ground, so I had to implement ground check in my script. The keys for moving left and right are either the left and arrow keys or the A and D on the keyboard, and the key for jumping is the space bar on the keyboard. I was finally able to get my character to move left, right, and jump when I started the game.

<iframe width="560" height="315" src="https://www.youtube.com/embed/wAS7bUFawS0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


# Setting Up Unity

My first milestone was setting up Unity and getting familiar with the Unity Editor as well as the sprites and background. I downloaded Unity Hub from the website where I then installed the Unity Editor. After installing the Unity Editor, I was able to then create my new Unity project, in which I selected 2D the Unity game since I am creating a 2D game and I named my project Pacman Isle as that is the name of the game I am planning to make by the end. I was then directed to the Unity Editor, which is where we make our games. I was new to Unity so I had to spend some time figuring out how the Unity Editor works. I then had to create a sprite sheet for the main character, which is Pacman! I used another software called GIMP (GNU Image Manipulation Program) to create a sprite sheet of closed mouth and open mouth Pacman as my game switches between closed mouth and open mouth Pacman. I then exported that sprite sheet to Unity and sliced each individual images (open mouth and closed mouth) through the Sprite Editor, where I was able to drag my main character to the Scene Window. I then got the background of my game from the Unity Asset Store and I organized the layout of the background through the Scene Window. I was finally able to switch to the Game Window and saw how the game would look like as it rendered the game objects, including the main character and the background.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Ec-3HJSqS9c" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
