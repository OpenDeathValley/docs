DVF
===

This type of file contains sprites and animation data.

File list
---------

* :file:`.\Game\Data\Animations\*`
* :file:`.\Game\Data\Characters\*`

Specifications
--------------

Structure
^^^^^^^^^

.. code-block:: text
    
    struct file_header
    for (file_header.num_sprites) {
        struct sprite_header
        data   sprite
    }
    struct objects_header
    for (objects_header.num_objects) {
        struct object
        for (object.num_animations) {
            for (object.num_perspectives) {
                struct animation
                for (animation.num_frames) {
                    struct frame
                }
            }
        }
    }
    
File Header
^^^^^^^^^^^

.. code-block:: text

    + 0x00:    Version     [WORD]
    + 0x02:    NUM_SPRITES [WORD]      // number of sprites
    + 0x04:    PADDING     [WORD]      // NOT USED
    + 0x06:    MAX_WIDTH   [WORD]      // max width of all sprites
    + 0x08:    MAX_HEIGHT  [WORD]      // max height of all sprites
    + 0x0a:    PADDING     [BYTE] * 20 // NOT USED
    
* Length header 0x1E
* Version must be equal to 0x200
    
Sprite Header
^^^^^^^^^^^^^

.. code-block:: text

    + 0x00:    SIZE        [DWORD]  // offset to next sprite
    + 0x04:    WIDTH       [WORD]   // width of the sprite (pixel)
    + 0x06:    HEIGHT      [WORD]   // height of the sprite (pixel)
    + 0x08:    UNKNOWN     [WORD]
    + 0x0a:    SPRITE      [BYTE] * (SIZE - 0xa [size of Sprite Header])
    
    
Sprite Data
^^^^^^^^^^^

For every row (height) in the sprite:

.. code-block:: text

    + 0x00:    NUM_TRANSPARENT_PIXELS  [WORD]
    + 0x02:    NUM_TOTAL_PIXELS        [WORD]

If NUM_TOTAL_PIXELS (int16_t) is -1, the whole line is transparent (color for transparent?). If NUM_TOTAL_PIXELS > -1, fill the first NUM_TRANSPARENT_PIXELS pixels with transparent. Read 2 byte long pixels (R5B6B5) for NUM_TOTAL_PIXELS times. Fill the remaining pixels (according to the sprite header's width) with transparent.

Objects Header
^^^^^^^^^^^^^^

.. code-block:: text

    + 0x00:    NUM_OBJECTS [WORD]   // number of objects

Object
^^^^^^

.. code-block:: text

    + 0x00:    NAME              [BYTE] * 32  // object name
    + 0x20:    NUM_PERSPECTIVES  [WORD]       // number of perspectives the object can be shown in
    + 0x22:    PADDING           [BYTE] * 32
    + 0x42:    NUM_ANIMATIONS    [WORD]       // number of animations available for the object
    + 0x44:    PADDING           [BYTE] * 16
    + 0x54:    MAX_WIDTH         [WORD]
    + 0x56:    MAX_HEIGHT        [WORD]
    + 0x58:    UNKNOWN0          [DWORD]
    + 0x5C:    UNKNOWN1          [DWORD]
    + 0x60:    PADDING           [BYTE] * 20
    
* Size of Object: 0x74

Animation
^^^^^^^^^

.. code-block:: text

    + 0x00:    PADDING           [BYTE] * 4
    + 0x04:    NUM_FRAMES        [WORD]
    + 0x06:    UNKNOWN0          [WORD]
    + 0x08:    UNKNOWN1          [WORD]
    + 0x0a:    UNKNOWN2          [DWORD]
    + 0x0e:    UNKNOWN3          [DWORD]
    + 0x12:    PERSPECTIVE_ID    [WORD]
    + 0x14:    ANIMATION_ID      [WORD]
    + 0x16:    ANIMATION_NAME    [BYTE] * 32

UNKNOWN0 to UNKNOWN3 don't seem to have any impact.

Frame
^^^^^

.. code-block:: text

    + 0x00:    SPRITE_ID         [WORD]
    + 0x02:    DURATION          [WORD]
    + 0x04:    DISTANCE          [WORD]
    + 0x06:    OFFSET_X          [WORD]
    + 0x08:    OFFSET_Y          [WORD]
    + 0x0a:    SOUND_EFFECT      [WORD]
    + 0x0c:    UNKNOWN5          [WORD]

DURATION is the time until the next frame is shown. This seems to be a multiple of 1/30 seconds.

DISTANCE is the distance the object covers while the animation displays the frame, 0 being the lowest distance, scaling upwards linear (might be a pixel unit or something arbitrary).

OFFSET_X and OFFSET_Y is the relative position between the object and the frame. Different frames from one animation have different sizes so to keep the object in the frames centered the position must be adjusted by OFFSET_X in X direction and OFFSET_Y in Y direction.

When the frame is displayed and the SOUND_EFFECT contains a valid sound effect ID (where are they? Is sound ID 0 possible?), the sound effect will be played.

UNKNOWN5 is ZERO in every file.