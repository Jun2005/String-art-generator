# String Art Generator
<img width="806" height="463" alt="string art" src="https://github.com/user-attachments/assets/6c8c64c9-d18c-478f-b7c1-f2dbacd979a3" />  

https://jun2005.github.io/StringArtGenerator/

This simple website creates string art from a chosen image. You can change the parameters to your liking.

### Number of pins:
- The number of points around the circular canvas from which a string/line can start. The larger the number, the more detailed the final art piece will be. It will also take longer to process the more pins there are.
### Number of strings:
- The number of lines on the canvas. Start small; you can add more string later, but you can't remove lines.
### String opacity:
- Adjusts the darkness of each line. Smaller numbers mean it will take more strings to form a well-defined image, but the final result can be a lot more detailed.
### String thickness:
- Generally speaking, it's best if this parameter is as small as possible. Too small and the line won't be visible, so try and fine-tune this parameter.
### Tips:
- If the generated art is blurry, try resizing the browser to be as large as possible and refresh the page. This will make the art piece render at a higher resolution.
- The final art piece may look better on higher contrast images.

# String art generation algorithm
1. Select a random pin to start at.
2. For every possible line that can be made from the starting point, calculate the score. The score is calculated as the average difference in brightness between the canvas and the image along a given line. Since we are working with pixels, I used Bresenham's line algorithm to approximate a line in pixels.
3. Find the line that results in the highest score and set the ending point of that line as the new starting point.
4. Draw the chosen line on the canvas.
5. Go back to step 2 if there are more strings to draw.

# Rooms for improvement
The current string art algorithm is extremely slow since it doesn't utilize parallelism, and in each iteration, the score for each line is calculated from the ground up. More sophisticated algorithms use Radon transform or Fourier transform.
