# Stable diffusion GUI

Date [HIDE]: November 10, 2022 12:32 AM
Без разбора: 106 дней
Добавлено: 10.11.2022
Разобрано: No
Ссылка: https://www.reddit.com/r/StableDiffusion/comments/yql810/update_170_of_my_windows_sd_gui_is_out_supports/?utm_source=share&utm_medium=android_app&utm_name=androidcss&utm_term=2&utm_content=share_button
Темы: ../%D0%A2%D0%B0%D0%B1%D0%BB%D0%B8%D1%86%D0%B0%20%E2%80%9C%D0%A2%D0%B5%D0%BC%D1%8B%E2%80%9D%205261d8ac365a4baa890082f78175e751/Stable%20Diffusion%201826c5402bdd451081c322e09681b21a.md

![sFlc0SzJVhEgSFKEtfsTBBxNeAILhTEga3-KQeKuL3U.jpg](Stable%20diffusion%20GUI%202a32c7cc3183475c8cbfd03942ef2c25/sFlc0SzJVhEgSFKEtfsTBBxNeAILhTEga3-KQeKuL3U.jpg)

1.7.0 Changelog:

- Added support for running multiple init images at once, e.g. for animation frames
- Added support for wildcards (insert words/phrases into prompt dynamically)
- Added "Hi-res Fix" which allows better results at higher (>512px) resolutions
- Added support for loading custom VAE models (can improve image quality)
- Added support for running upscaling or face restoration manually
- Added support for all samplers when using an init image (not just DDIM)
- Added button to resize the window to fit the currently displayed image
- Added option to save output images in a subfolder per session
- Added options to use seamless mode only on one axis (horizontal or vertical)
- Added a label that displays the current image's prompt
- Added hotkeys: Quick-switch VAE, copy current image, copy image to favorites
- Added new developer tool: Open CMD in SD Conda environment
- DreamBooth training: Images can now be automatically resized if they are not 512x512
- DreamBooth training: Added slider for steps multiplier (0.5x-2x)
- GUI improvements, prompt and negative prompt are now separate
- Image viewer now also shows "actual" image resolution (for upscaled images)
- Sliders now also allow you to type a value instead of dragging the handle
- Loading image metadata now also works for images generated with automatic1111
- "Delete All Current Images" now requires a confirmation
- Improved prompt history/queue UI (show full prompt on hover, and more)
- Improved GUI rendering, should have less flickering now
- Fixed bug where model pruning would say "Failed..." even if it was successful
- Support for RunwayML inpainting
- Automatically run all possible wildcard combinations when using multiple wildcards in a prompt
- More!

**The download includes SD 1.5 and the latest StabilityAI VAE model.**

Awesome work as always! Still my way to go SD GUI, thank you so much for putting so much effort on this.

I really appreciate the separation of prompts (normal and negative), I think it's a huge QOL improvement. May I suggest adding a "Skip last N layers of CLIP model" for a future update?

Trying this for the first time. Is there any way to see a preview of the image as it's being generated with this GUI? I really like seeing the progress of the image creation before the final state. Sometimes you just know it's not going to turn out as expected and want to abort, but it's also just fun to watch images slowly come into focus.

In general though, great job at simplifying things. This is well laid out and much more accessible for people not familiar with running python or notebooks.

Checking it out!!

I'm confused, I had a different bookmark saved to a different GUI under NMKD that is totally different than this. Now I can't find where I got that one. Too many atomic fireballs is what I blame.

Automatic's has been crashing like crazy on me lately, error after error trying to update and do this and that, even after a fresh clean install, so yay more options. Hopefully inpainting works.

Apparently the other is cmdr2's Stable UI. Now I've got webui, gui and stable ui.

I'd really like to be able to designate my model folder unless this update allows it. I drifted away from this UI for awhile because I couldn't shortcut to or designate the model folder shared by other things. Don't really know python so wasn't brave enough to break into the code.

This was the first UI I used with SD and I LOVED annoying my neighbor with the completion bell sound, my neighbor is a cee you next Tuesday.