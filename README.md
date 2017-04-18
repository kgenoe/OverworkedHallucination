# Overworked Hallucination

Overworked Hallucination was my 2017 WWDC Scholarship entry. It was created in my (limited) free time during March of 2017. Note that this is both the first SpriteKit game and first playground I have made. As such, please do not consider the code quality to be an accurate representation of my ability.

## Plot
A girl named Erica exhausts herself working on her WWDC Scholarship application. After a late night of coding, she falls asleep at her desk and dreams that she’s trapped in Xcode! She has to dodge red errors (enemies) while jumping on lines of code (platforms) and collecting bits (coins). 

## Mechanics
The goal of the game is simple, set a high score. The score increases by 1 every 50 milliseconds. Additionally, the score increases by 100 every time Erica collects a bit. Controls for the game are relatively basic. Tap the screen to jump and swipe the screen to flip gravity. There are also two buttons below the game scene that can be used to play the game without gestures. The game ends when Erica touches a red error. 

## Customization
From the left view in the playground, you can customize Erica’s world. You can control the number of times Erica can jump before touching the ground or another platform, how fast Erica runs, whether Erica can flip gravity, the frequency errors appear, and the frequency platforms appear. You can also customize the lines of code that make up platforms. Note that the playground was only tested on a Mac, as unfortunately I did not have access to an iPad for testing.

## Development
The primary technology used in my playground is SpriteKit. The majority of the interactions are powered by SpriteKit’s physics engine. SpriteKit’s native collision detection is used to detect contact between Erica and errors, code lines and bits. I had to write a custom override for Erica’s interaction with the platforms to get the desired behaviour of being able to pass through them in one direction, which ended up being the most challenging part of the project. Originally I had used AVPlayer for the sound effects, but SpriteKit’s native playSoundFileNamed action had much better performance so I switch to using SKActions for sound instead. 

For the platforms, I wanted to be able to dynamically create any line of Swift code and have it render with the proper colors from the Xcode Dusk theme. This required writing a rudimentary parser for the Swift language that can pick out comments, characters, strings, numbers, urls, keywords, types, and class names to style them with the appropriate colors. The parser used basic regular expressions and some fairly complex string processing to style an NSMutableAttributedString. I then had to make a custom SKNode that was capable of displaying an NSMutableAttributedString, as SpriteKit does not support it natively.

Finally, I wanted lines of code to pass in the background, that created a parallax effect that made the world seem a bit more alive. Because of the way I had designed the row structure, it was relatively easy to create a node similar to the platform, but with 3 presets for opacity, speed, and text size to create 3 additional levels of depth. Visually, it’s my favourite part about the project.
