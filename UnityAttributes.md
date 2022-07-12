# Unity Attributes

## SerializeFields

`[SerializeField]` - make variable changable in unity inspector even if variable is private.

**Example :** 

		[SerializeField] private float PriceOfHouse;

## Headers

`[Header("Name")]` - Make header/title for block of variables.

**Example :**

		[Header("Movement")]
		public float runSpeed;
		public float jumpForce;
		public float dashSpeed;
**Result :**
![Headers Result In Inspector](https://github.com/Pixtane/UnityStuff/blob/main/Images/Headers.png?raw=true)
## Spaces

`[Space(20)]` - Make a space between variables, use pixels.<br>
**Note :** Use them to separate block of codes in Header or between end of one header and start of another.

Example:

		[Header("Movement")]
		public float runSpeed;
		public float dashSpeed;
		[Space(20)]
		public float jumpForce;
**Result :**
![Spaces Result In Inspector](https://github.com/Pixtane/UnityStuff/blob/main/Images/Spaces.png?raw=true)


## Number ranges

`[Range(0f, 25f)]` - Make a slider for float, int or double variable and make maximum and minimum for them.
**Note :** first is minimum, second - maximum.

**Example :**

		[Range(0f, 100f)] public float runSpeed;
		[Range(0f, 75f)] public float dashSpeed = 15f;
**Result :**
![Ranges Result In Inspector](https://github.com/Pixtane/UnityStuff/blob/main/Images/Ranges.png?raw=true)


## Tooltips

`[Tooltip("Some stuff")]` - ToolTip for variable.

**Note :** It only applies to only one next varible. Better place this attribute in previous line to save space and to organize. The next variable will show this message when you place mouse in it inside inspector.

**Example :**

		[Tooltip("Speed for player walk")] public float runSpeed;
		[Tooltip("Speed of player dashing. The less value the slower is dash. The distance is always the same")]
		public float dashSpeed = 15f;
**Result :**
![Ranges Result In Inspector](https://github.com/Pixtane/UnityStuff/blob/main/Images/ToolTips.png?raw=true)


## Enumerators

`enum` - This is not attribute, but it very useful. Use them for list of object that you can choose from.

**Example :**

		public enum Games { Terraria, Minecraft, Fortnite, Other };
		
		public class PlayerMovement : MonoBehaviour
		{	
			[SerializeField] Games YourBestGame;
		}
**Result :**
![Ranges Result In Inspector](https://github.com/Pixtane/UnityStuff/blob/main/Images/Enum.png?raw=true)

# Script Example

	using System.Collections;
	using System.Collections.Generic;
	using UnityEngine;
	using UnityEngine.Events;

	public enum CharacterTypes { Commander, Engineer, Medic, Botanist, Marine };


	public class PlayerController : MonoBehaviour
	{
	    [Tooltip("This is the type of player character that was created")]
	    [SerializeField] private CharacterTypes characterType;
	    [Tooltip("This is the players custom biography")]
	    [TextArea] [SerializeField] private string playerBio;

	    [Header("UI")]
	    [Tooltip("This is a reference to the character stats panel on the user interface")]
	    [SerializeField] private GameObject characterStatsPanel;
	    [Tooltip("This is the sprite that will be displaye don the stats panel for the players avatar")]
	    [SerializeField] private Sprite characterAvatar;
	    [Space(20)]

	    [Header("Locomotion")]
	    [Range(0f,25f)] [SerializeField] private float runSpeed;
	    [Range(0f, 5f)] [SerializeField] private float crouchSpeed;
	    [Range(10f, 15f)] [SerializeField] private float moveSpeed;
	    [Range(10f, 15f)] [SerializeField] private float rotateSpeed;
	    [Range(10f, 15f)] [SerializeField] private float jumpSpeed;
	    [Range(10f, 15f)] [SerializeField] private float jumpHeight;
	    [Space(10)]

	    [Header("Combat")]
	    [Range(10f, 15f)] [SerializeField] private float attackRange;
	    [Range(10f, 15f)] [SerializeField] private float attackSpeed;
	    [Space(10)]


	    [Header("Particles")]
	    [SerializeField] private GameObject bloodSplatterParticles;
	    [SerializeField] private GameObject healingParticles;
	    [SerializeField] private GameObject moraleParticles;
	    [Space(10)]

	    [Header("Sounds")]
	    [SerializeField] private AudioClip hitSound;
	    [SerializeField] private AudioClip deathSound;
	    [SerializeField] private AudioClip healSound;
	    [Space(10)]

	    [Header("Health")]
	    [SerializeField] private int maxHealth = 100;
	    [SerializeField] private int currentHealth = 50;
	    [Space(10)]

	    [Header("Unity Events")]    
	    [SerializeField] private UnityEvent onSelected = null;    
	    [SerializeField] private UnityEvent onDeselected = null;
	}
> Code example is from this github file : https://github.com/MetalStormProductions/YoutubeVideos/blob/main/PlayerController.cs
> Video :
> https://www.youtube.com/watch?v=6I4SYU1JU5g
