[Homepage](./index.md)

# Make Your Own Computer Game
This project is to make a computer game with Unity. The game can be anything and in the cases of this project, I am making a 2d game called Pacman Isle which is a platformer game just like Super Mario Bros.  

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Arnesh K | Irvington High School | Software Engineering | Incoming Senior

<iframe mozallowfullscreen="true" allow="autoplay; fullscreen" src="https://arneshkumar.github.io/arneshbluestamp/PacmanGame/index.html" style="border:0px #000000 none;" name="My Game" scrolling="no" msallowfullscreen="true" allowfullscreen="true" webkitallowfullscreen="true" allowtransparency="true" frameborder="0" marginheight="px" marginwidth="320px" height="500px" width="700px"></iframe>

# Demo Night

Here is the Demo Night for my project, which is the Make Your Own Computer Game!

# Side-scroller, Enemies, Main Menu, Game Over Screen, Congratulations Screen, and Audio

My third and final milestone was getting the side-scroller aspect, enemies, main menu, game over and congratulations screen, and audio to work. I first created the script for the side-scroller by setting the transform position equal to the x-axis position of the player, leaving the y-axis and z-axis as is, then attaching the script to the Main Camera. I then created the enemies by using the pacman ghost sprite sheet online and slicing each of the pacman ghosts, all 4 colors and each facing in different directions, totalling 16 pacman ghosts. I had to also create the animations for each of the pacman ghosts depending on the movement, which took time to get through because each of the pacman ghost colors act differently. After getting the pacman ghosts to move accordingly, I decided to make additional touches by adding the super jump powerup which allows the main character to jump high, and the X sign at the start of the game. For the pacman ghosts and the power up, I had to add colliders so that there can be collision detected with the main character. After figuring out the functionality of the enemies, I made the Main Menu screen by creating a new scene called Menu through which I designed the title and buttons. In addition, I created the Game Over Screen and Congratulations Screen which were similar processses, so that once I was able to design one of the screens, I was able to design other two quicker. The main problem was figuring out how to create the screens and layout so in order to figure that out, I had to research online and learn the process, utilizing the UI Game Object. After creating the screens, I got audio clips from online and implemented them into the game. The main problem was that I could not reference multiple audio sources in the script so I created an array of audio sources so that I could index into the array in my script. After getting that to work, I basically added a finish line at the end of the game to indicate the end of the game. I was finally able to complete my game which turned out to be decently difficult in the end!

<iframe width="560" height="315" src="https://www.youtube.com/embed/eSKkiKTcQrs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Character Moving Left, Right, and Jumping

My second milestone was getting my character to move left, right, and jump where I had to make the C# script. I added the Rigidbody2D component to Pacman in order to allow it to react to real time physics, which is, in this case, gravity. I added a circle collider 2D to Pacman and box collider 2d to the ground so that there can be collision detected between the character and ground, and so that the character jumps and does not fall right below the ground. I then had to write the C# script to get my character moving left, right, and jumping. The main way I wanted my character to move was to flip the Pacman when switching to different directions (either left or right). After writing the C# script, my character was moving slowly and rotating, so in order to fix that problem, I had to talk with my instructor and I was able to figure out how to stop the rotation and make my character move faster. I also had to use the Animator tab to create the idle animation (Pacman closed mouth) and the moving animation (Pacman closed mouth and open mouth). In my C# script, I had to also talk with my instructor in order to figure out how to play the animation states depending on if my character is moving or not. In addition, after getting my character to move left, right, and jump, I also had to figure out when my character should be able to jump which is when the character is on the ground, so I had to implement ground check in my script. The keys for moving left and right are either the left and arrow keys or the A and D on the keyboard, and the key for jumping is the space bar on the keyboard. I was finally able to get my character to move left, right, and jump when I started the game.

<iframe width="560" height="315" src="https://www.youtube.com/embed/wAS7bUFawS0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


# Setting Up Unity

My first milestone was setting up Unity and getting familiar with the Unity Editor as well as the sprites and background. I downloaded Unity Hub from the website where I then installed the Unity Editor. After installing the Unity Editor, I was able to then create my new Unity project, in which I selected 2D the Unity game since I am creating a 2D game and I named my project Pacman Isle as that is the name of the game I am planning to make by the end. I was then directed to the Unity Editor, which is where we make our games. I was new to Unity so I had to spend some time figuring out how the Unity Editor works. I then had to create a sprite sheet for the main character, which is Pacman! I used another software called GIMP (GNU Image Manipulation Program) to create a sprite sheet of closed mouth and open mouth Pacman as my game switches between closed mouth and open mouth Pacman. I then exported that sprite sheet to Unity and sliced each individual images (open mouth and closed mouth) through the Sprite Editor, where I was able to drag my main character to the Scene Window. I then got the background of my game from the Unity Asset Store and I organized the layout of the background through the Scene Window. I was finally able to switch to the Game Window and saw how the game would look like as it rendered the game objects, including the main character and the background.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Ec-3HJSqS9c" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Development Environment Using Windows 10

|:--:|:--:|:--:|
| **Application** | **Description** | **Cost**
|:--:|:--:|:--:|
| Unity | Making the Unity Game | Free
|:--:|:--:|:--:|
| GIMP (GNU Image Manipulation Program) | Designing the Sprites | Free

# Schematics
![Platform Schematic](https://user-images.githubusercontent.com/82551067/180573692-31c6e1eb-1937-4be3-911e-523261d9906d.png)

# Final Code
```c#
// CameraController.cs

using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class CameraController : MonoBehaviour
{
    public GameObject player;

    // Update is called once per frame
    void Update()
    {
        transform.position = new Vector3(player.transform.position.x, transform.position.y, transform.position.z);
    }
}
```

```c#
// CongratulationsScreen.cs

using UnityEngine;
using UnityEngine.UI;
using UnityEngine.SceneManagement;

public class CongratulationsScreen : MonoBehaviour
{
    [SerializeField] GameObject congratulationsScreen;

    public void SetCongratulations()
    {
        congratulationsScreen.SetActive(true);
        Time.timeScale = 0;
    }

    public void RestartGame()
    {
        Time.timeScale = 1;
        SceneManager.LoadScene("Example");
    }

    public void ReturnMenu()
    {
        SceneManager.LoadScene("Menu");
    }
}
```

```c#
// EnemyControllerAllDirections.cs

using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class EnemyControllerAllDirections : MonoBehaviour
{
    public float speed = 3f;
    Animator anim;

    Vector3 pos;
    Vector3[] points; 
    private int nextPointIndex = 0;

    // Start is called before the first frame update
    void Start()
    {
        pos = transform.position;
        anim = GetComponent<Animator>();
        points = new [] { new Vector3(pos.x, pos.y, pos.z), new Vector3(pos.x - 3, pos.y, pos.z), new Vector3(pos.x - 3, pos.y + 5, pos.z), new Vector3(pos.x, pos.y + 5, pos.z) };
    }

    // Update is called once per frame
    void Update()
    {
        pos = transform.position;
        bool reachedNextPoint = (pos == points[nextPointIndex]);
        if (reachedNextPoint)
        {
            nextPointIndex++;
            if (nextPointIndex >= points.Length)
            {
                nextPointIndex = 0;
            }
        }
        if (nextPointIndex == 0)
        {
            anim.Play("facingDownRectangle");
        }
        if (nextPointIndex == 1)
        {
            anim.Play("facingLeftRectangle");
        }
        if (nextPointIndex == 2)
        {
            anim.Play("facingUpRectangle");
        }
        if (nextPointIndex == 3)
        {
            anim.Play("facingRightRectangle");
        }
        transform.position = Vector3.MoveTowards(pos, points[nextPointIndex], speed * Time.deltaTime);
    }
}
```

```c#
// EnemyControllerDisappear.cs

using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class EnemyControllerDisappear : MonoBehaviour
{
    public float speed = 10f;
    Animator anim;

    Vector3 pos;
    Vector3[] points; 
    private int nextPointIndex = 0;

    // Start is called before the first frame update
    void Start()
    {
        pos = transform.position;
        anim = GetComponent<Animator>();
        points = new [] { new Vector3(pos.x, pos.y, pos.z), new Vector3(pos.x - 5, pos.y, pos.z), new Vector3(pos.x - 5, pos.y + 10, pos.z), new Vector3(pos.x, pos.y + 10, pos.z) };
    }

    // Update is called once per frame
    void Update()
    {
        pos = transform.position;
        bool reachedNextPoint = (pos == points[nextPointIndex]);
        if (reachedNextPoint)
        {
            nextPointIndex++;
            if (nextPointIndex >= points.Length)
            {
                nextPointIndex = 0;
            }
        }
        if (nextPointIndex == 0)
        {
            anim.Play("disappearFacingDown");
        }
        if (nextPointIndex == 1)
        {
            anim.Play("disappearFacingLeft");
        }
        if (nextPointIndex == 2)
        {
            anim.Play("disappearFacingUp");
        }
        if (nextPointIndex == 3)
        {
            anim.Play("disappearFacingRight");
        }
        transform.position = Vector3.MoveTowards(pos, points[nextPointIndex], speed * Time.deltaTime);
        if (Time.fixedTime%.5 < .4)
        {
            GetComponent<Renderer>().enabled = false;
        }
        else 
        {
            GetComponent<Renderer>().enabled = true;
        }
    }
}
```

```c#
// EnemyControllerLeftRight.cs

using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class EnemyControllerLeftRight : MonoBehaviour
{
    float speed = 2f;
    float width = 5f;
    Animator anim;
    Vector3 pos;

    // Start is called before the first frame update
    void Start()
    {
        anim = GetComponent<Animator>();
        pos = transform.position;
    }

    // Update is called once per frame
    void Update()
    {
        float offSetX = Mathf.Cos(Time.time * speed);
        transform.position = new Vector3(pos.x + (offSetX * width), pos.y, pos.z);
        if (offSetX >= 0.92)
        {
            anim.Play("pacmanLeft");
        }
        else if (offSetX <= -0.92)
        {
            anim.Play("pacmanRight");
        }
    }
}
```

```c#
// EnemyControllerUpDown.cs

using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class EnemyControllerUpDown : MonoBehaviour
{
    float speed = 3f;
    float height = 4f;
    Animator anim;
    Vector3 pos;

    // Start is called before the first frame update
    void Start()
    {
        anim = GetComponent<Animator>();
        pos = transform.position;
    }

    // Update is called once per frame
    void Update()
    {
        float offSetY = Mathf.Sin(Time.time * speed);
        transform.position = new Vector3(pos.x, pos.y + (offSetY * height), pos.z);
        if (offSetY >= 0.92)
        {
            anim.Play("pacmanDown");
        }
        else if (offSetY <= -0.92)
        {
            anim.Play("pacmanUp");
        }
    }
}
```

```c#
// GameOverManager.cs

using UnityEngine;
using UnityEngine.UI;
using UnityEngine.SceneManagement;

public class GameOverManager : MonoBehaviour
{
    [SerializeField] GameObject gameOverScreen;

    public void SetGameOver()
    {
        gameOverScreen.SetActive(true);
        Time.timeScale = 0;
    }
    
    public void RestartGame()
    {
        Time.timeScale = 1;
        SceneManager.LoadScene("Example");
    }

    public void ReturnMenu()
    {
        SceneManager.LoadScene("Menu");
    }
}
```

```c#
// MainMenu.cs

using UnityEngine;
using UnityEngine.UI;
using UnityEngine.SceneManagement;

public class MainMenu : MonoBehaviour
{
    [SerializeField] GameObject mainMenuScreen;
    
    public void PlayGame()
    {
        SceneManager.LoadScene("Example");
        Time.timeScale = 1;
    }

    public void QuitGame()
    {
        Application.Quit();
    }
}
```

```c#
// PlayerController.cs

using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.SceneManagement;

public class PlayerController : MonoBehaviour
{
    public float maxSpeed = 100f;
    public float jumpSpeed = 8f;
    bool facingRight = true;
    Rigidbody2D rb;
    Animator anim;
    public AudioSource[] audio = new AudioSource[3];
    
    public Transform groundCheck;
    public float groundCheckRadius;
    public LayerMask groundLayer;
    private bool isTouchingGround;

    [SerializeField] GameOverManager gameOverManager;
    [SerializeField] CongratulationsScreen congratulationsManager;

    // Start is called before the first frame update
    void Start()
    {
        rb = GetComponent<Rigidbody2D>();
        anim = GetComponent<Animator>();
    }

    // Update is called once per frame
    void Update()
    {
        isTouchingGround = Physics2D.OverlapCircle(groundCheck.position, groundCheckRadius, groundLayer);
        float move = Input.GetAxis("Horizontal");
        anim.enabled = true;
        if (!(rb.velocity.magnitude > 0))
        {
            anim.Play("pacmanIdle");
        }
        else
        {
            anim.Play("pacmanAnimation");
        }
        rb.velocity = new Vector3(move * maxSpeed * 4, rb.velocity.y);
        rb.freezeRotation = true;
        if (move < 0 && facingRight)
        {
            Flip();
        }
        else if (move > 0 && !facingRight)
        {
            Flip();
        }
        if (Input.GetButtonDown("Jump") && isTouchingGround)
        {
            audio[0].Play();
            rb.velocity = new Vector3(rb.velocity.x, jumpSpeed);
        }
    }

    // Flip if needed
    void Flip()
    {
        Vector3 theScale = transform.localScale;
        theScale.x *= -1;
        transform.localScale = theScale;
        facingRight = !facingRight;
    }

    void OnCollisionEnter2D(Collision2D coll)
    {
        for (int i = 1; i < 9; i++)
        {
            if (coll.gameObject.name == ("pacManGhost " + i) || coll.gameObject.name == "off the map")
            {
                audio[1].Play();
                gameOverManager.SetGameOver();
                jumpSpeed = 8f;
            }
        }
        if (coll.gameObject.name == "superjump icon")
        {
            jumpSpeed = (float) (1.75 * jumpSpeed);
        }
        if (coll.gameObject.name == "finish line")
        {
           audio[2].Play();
           congratulationsManager.SetCongratulations();
           jumpSpeed = 8f;
        }
    }
}
```

```c#
// PowerUp.cs

using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class PowerUp : MonoBehaviour
{
    void OnCollisionEnter2D(Collision2D coll)
    {
        if (coll.gameObject.name == "pacMan16_0")
        {
            Destroy(gameObject);
        }
    }
}
```
