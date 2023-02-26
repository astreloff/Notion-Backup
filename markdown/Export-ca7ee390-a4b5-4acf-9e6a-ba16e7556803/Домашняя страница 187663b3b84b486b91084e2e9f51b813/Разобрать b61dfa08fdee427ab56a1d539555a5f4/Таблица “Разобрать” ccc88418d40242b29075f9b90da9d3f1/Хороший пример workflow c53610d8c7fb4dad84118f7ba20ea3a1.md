# Хороший пример workflow

Date [HIDE]: November 9, 2022 3:44 PM
Без разбора: 108 дней
Добавлено: 09.11.2022
Разобрано: No
Ссылка: https://www.reddit.com/r/StableDiffusion/comments/yog3c2/my_workflow/?utm_source=share&utm_medium=android_app&utm_name=androidcss&utm_term=14&utm_content=share_button
Темы: ../%D0%A2%D0%B0%D0%B1%D0%BB%D0%B8%D1%86%D0%B0%20%E2%80%9C%D0%A2%D0%B5%D0%BC%D1%8B%E2%80%9D%205261d8ac365a4baa890082f78175e751/Stable%20Diffusion%201826c5402bdd451081c322e09681b21a.md

```
..., (humorous illustration, hyperrealistic, big depth of field, colors, whimsical cosmic night scenery, 3d octane render, 4k, concept art, hyperdetailed, hyperrealistic, trending on artstation:1.1)
Negative prompt: text, b&w, (cartoon, 3d, bad art, poorly drawn, close up, blurry, disfigured, deformed, extra limbs:1.5)
Steps: 20, Sampler: DPM++ 2M Karras, CFG scale: 5, Size: 512x704

```

```
Gal Gadot as (Wonder Woman:0.8), (humorous illustration, hyperrealistic, big depth of field, colors, whimsical cosmic night scenery, 3d octane render, 4k, concept art, hyperdetailed, hyperrealistic, trending on artstation:1.1)

```

NB: I mix around with models. I like the spiderverse model a lot and most of the images are with that model. I found that using styled models for other than their intended use works great.

1. Create a base image with 512x704 with above base prompt. CFG at 5.
2. Optional: Inpaint out if needed
3. Optional: Inpaint out if needed

The base prompt certainly has room for improvements. But I found it to work quite well. I don't use any eye restoration. Just SD and upscaling.

PS: Don't over expose your subject. "Gal Gadot as Wonder Woman" can give a bit blurry result. Try "Gal Gadot as (Wonder Woman:0.8)" instead.

PS2: I use this VAE on all my models: [r/StableDiffusion](https://www.reddit.com/r/StableDiffusion/)/comments/yaknek/you_can_use_the_new_vae_on_old_models_as_well_for/

With 5 I seem to get "better noise" in the image. As in they look more realistic. With higher they get more stylized.

As with all parameters, feel free to play around with the CFG. It's just so many different parameters to play with 😅

I think the most important settings I use are the two resolutions. Base 512x704 and 704x1024. These seem to produce coherent results quite often.

> cute fluffy adorable puppy, (illustration, hyperrealistic, big depth of field, colors, whimsical cosmic night scenery, 3d octane render, 4k, concept art, hyperdetailed, trending on artstation:1.1), (arcane style:1.4) Negative prompt: text, b&w, (cartoon, 3d, bad art, poorly drawn, close up, blurry, disfigured, deformed, extra limbs:1.5) Steps: 20, Sampler: DPM++ 2M Karras, CFG scale: 5, Seed: 3869826356, Size: 512x704, Model: Arcane
> 

[https://imgsli.com/i/050d27fc-ceeb-432f-998f-9bde3bda1896.jpg](https://imgsli.com/i/050d27fc-ceeb-432f-998f-9bde3bda1896.jpg)

> cute fluffy adorable puppy, (illustration, hyperrealistic, big depth of field, colors, whimsical cosmic night scenery, 3d octane render, 4k, concept art, hyperdetailed, trending on artstation:1.1) Negative prompt: text, b&w, (cartoon, 3d, bad art, poorly drawn, close up, blurry, disfigured, deformed, extra limbs:1.5) Steps: 20, Sampler: DPM++ 2M Karras, CFG scale: 5, Seed: 3869826356, Size: 512x704, Model: Spiderverse
> 

[https://imgsli.com/i/2032dc51-267d-4467-9982-dd619d7001ce.jpg](https://imgsli.com/i/2032dc51-267d-4467-9982-dd619d7001ce.jpg)

When people say "Mix models" do they mean just swapping models as you img 2 img? When they say 70%Sd 1.5 30% Robodiffusion, is there a lever to automate that, or do you just guess?

I like what you got out of it! Each has character and presence. The wonky unicorn pose makes sense, and that's cool.

I just use one model at a time. Most of these are just using the spiderverse model.

But this one started with the spiderverse model on txt2img, and then arcane model + "(arcane style:1.4)" in img2img: [https://preview.redd.it/3zu1qsmhghy91.png?width=1408&format=png&auto=webp&s=9222f35b0caf731cfd2b69bb46a522dd100afb2f](https://preview.redd.it/3zu1qsmhghy91.png?width=1408&format=png&auto=webp&s=9222f35b0caf731cfd2b69bb46a522dd100afb2f)

I actually wondered about that, when I first saw it. It turns out that you can actually combine models (!) via checkpoint merger.

Now, I'm no expert, and I can't fathom how much time and trial/error would one have to go through before confidently exclaiming that, yes, this ratio of model A and model B is actually better than either on its own.

I found this one ([link](https://rentry.org/berrymix)) going around. If anything else, at least you can use it as a makeshift guide of how the whole thing works.

> a photo of a very cute bady dog, esao andrews, humorous illustration, hyperrealistic, big depth of field, colors, 3 d octane render, 4 k, concept art, hyperdetailed, hyperrealistic, trending on artstation Negative prompt: text, b&w, weird colors, (cartoon, 3d, bad art, poorly drawn, close up, blurry:1.5), (disfigured, deformed, extra limbs:1.5) Steps: 50, Sampler: DPM++ 2M Karras, CFG scale: 5, Seed: 2530519074, Size: 512x704, Model hash: ccf3615f
> 

This one with Modern Disney model gives this: [https://imgsli.com/i/34948094-9dac-4185-ab39-4f0aab462263.jpg](https://imgsli.com/i/34948094-9dac-4185-ab39-4f0aab462263.jpg)

Then I just used inpaint to remove the third paw, and img2img to get a higher size.

What does inpaint out mean in this context? What are you inpainting? Or are you trying to remove things? Furthermore, what are you img2img-ing? Like, are you taking less good images, and then just running them through img2img with the same prompt, just with a different size?