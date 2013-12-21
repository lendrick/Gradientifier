Gradientifier
=============

A tool that genreates color ramps for pixel art by simulating lighting conditions

Licensing
=========
My original intent was to release this code under the more liberal MIT license, however since I'm linking to farbtastic (which is GPLed), this code needs to be GPLed as well.  If you want to use this code under the MIT license, you have my permission to do so if you remove the dependency on farbtastic and replace it with another color picker.

Holy crap, what do all these crazy sliders to??
===============================================

Note that the below documentation is for rainbow mode.

Tint Color:
  It is possible to tint your entire rainbow at once with a single color.  Just change this color to whatever you want to use to tint the palette, and adjust the "Tint" slider under "Rainbow controls" until it's tinted as much as you want it to be.
  
Highlight color & Ambient color:
  These two sliders control the overall lighting conditions.  The "highlight" is a bright overhead light, which affects color where your object is lit brightly, while the "ambient light" is the light from the surroundings, which affects the color of shadows.  Generally, your highlight color should be brighter than your ambient color, or your results may not make a lot of sense.
  
Selected rainbow color:
  You can select a rainbow color by clicking on that color in the rainbow.  Then, you can use this color picker to change that color to whatver you'd like.
    
Reflectivity:
  A little bit of theory about lighting is necessary to understand this.  When you shine a light on a completely non-reflective object, the color of the object will be the red, green, and blue compoents of the objects color times the red, green, and blue components of the color of the light.  This means the following things:
  
    * If you shine a completely blue light on a completely red object, the color of the object will appear to be black, because the color of your light is rgb(0, 0, 1) and the color of your object is rgb(1, 0, 0), so the multiplied color will be rgb(0, 0, 0).
    * If you shine a completely blue light on a completely white object, the color of the object will appear to be blue, because the color of your light is rgb(0, 0, 1) and the color of your object is rgb(1, 1, 1), so the multiplied color will be rgb(0, 0, 1).
    
  Essentially, the way it works when you light a colored object is that the object absorbs all of the component colors in the light, except for the color of the object itself, which is reflected back.
  
  However, reflection changes the dynamic a little bit.  If an object is 100% reflective, it acts like a perfect mirror and bounces all light back without absorbing any.  For our purposes, that means we return a weighted average of the color of the object as if it's lit by the light, and the color of the light itself.  If an object is completely reflected, the object's color doesn't matter at all, and it acts like a mirror.  
  
Illumination:
  The illumination slider controls how much of the object is lit by the light source versus the ambient light.  An object with low illumination will be mostly dark, but with a bright highlight.  An object with high illumination will be mostly bright, but will still have a dark shadow.  Generally, the illumination slider is best used for creating dark, dramatic lighting with bright highlights.
  
Highlight multiplier:
  A little bit more theory is necessary here.  When you display pixels on a computer screen, the brightness of the rgb components of the pixel are clamped between the minimum and maximum intensity that your screen can put out.  While it's impossible for anything to be darker than black, in the real world, there's no practical limit to how bright a light source can be.  The Highlight Multiplier slider increases the intensity of your highlight color to values above 1 for the purpose of color ramp calculations.  After the color ramp is calculated, the values for the ramp are then clamped to a maximum of 1.  Be careful when adjusting the highlight multiplier, as it can make your ramps very bright very quickly.  It's often best used in conjunction with darker illumination, to bring out the color of the light in your highlights.
  
Brightness:
  This slider makes your entire ramp (both shadows and highlights) darker or lighter.
  
Contrast:
  This slider widens the contrast between your shadows and highlights.
  
Tint:
  This slider tints your entire rainbow with the selected tint color.

Desaturate:
  This slider tints your entire rainbow with white.

Darken: 
  This slider tints your entire rainbow with black.
  
For instance, if you want to make your rainbow more grey, you could slide the desaturate slider and the darken slider both part way up, or you could select a grey tint color and use the tint slider.  Technically the Desaturate and Darken sliders are somewhat redundant, but they allow you to make quick adjustments without messing with your tint.

So I like my palette, now what?
===============================

Right click on the swatches and save the image, then load it into your favorite pixel editing program.  Note that the top colors in the swatch image are always your rainbow colors, and aren't part of the DB32 palette.  They are provided for reference, because it's not always obvious from looking at a color ramp what the perceived color will be.
