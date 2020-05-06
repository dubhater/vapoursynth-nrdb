Description
===========

NRDB is a debanding function for VapourSynth. It removes the noise in the input clip, debands, and adds the noise back.

This is a port of the Avisynth function of the same name.


Usage
=====
::

    NRDB(input[, deband="", range, db_Y=64, db_Cb=0, db_Cr=0, grainY=0, grainC=0, dynamic_grain=False, keep_tv_range=False, nr="", planes=[0], sigma=4.0, sigma2=4.0])


Parameters:
    *input*
        A clip to process.
        
    *deband*
        Custom debanding filter/function. It must be either a filter from a binary plugin, or a function from a module that can be imported. Use like so::
        
            result = NRDB(video, deband="module.awesome_debanding_function(input={clip}, planes={planes})")
        
        or::
        
            result = NRDB(video, deband="core.awesome.DebandingFilter(clip={clip}, planes={planes})")
        
        If the custom debanding filter doesn't take a parameter called "planes" then that part can be omitted::
        
            result = NRDB(video, deband="core.awesome.DebandingFilter(clip={clip})")
        
        Pass "nop()" to disable the debanding stage.
        
        Default: empty.
        
    *range*
        f3kdb parameter.
        
        Increase to make it deband more.
        
        Default: 9 for resolutions up to 1024x576, 12 for resolutions up to 1280x720, and 15 for higher resolutions.
        
    *db_Y*, *db_Cb*, *db_Cr*
        f3kdb parameters.
        
        Increase to make it deband more.
        
        Default: 64, 0, 0.
        
    *grainY*, *grainC*
        f3kdb parameters.
        
        Increase to make it add more grain.
        
        Default: 0.
    
    *dynamic_grain*
        f3kdb parameter.
        
        Controls whether the added grain should be the same pattern in every frame or not.
        
        Default: False.
        
    *keep_tv_range*
        f3kdb parameter.
        
        Controls whether the pixel values should be clamped to TV range.
        
        Default: False.
        
    *nr*
        Custom noise reduction filter/function. Use it the same way as the deband parameter.
        
        Pass "nop()" to disable the noise reduction stage.
        
        Default: empty.
        
    *planes*
        Which planes to filter. Unfiltered planes will be copied.
        
        Default: 0.
        
    *sigma*, *sigma2*
        DFTTest parameters.
        
        Default: 4.0, 4.0.


Requirements
============

   * `DFTTest   <https://github.com/HomeOfVapourSynthEvolution/VapourSynth-DFTTest>`_
   * `F3KDB     <https://github.com/SAPikachu/flash3kyuu_deband>`_


License
=======

???
