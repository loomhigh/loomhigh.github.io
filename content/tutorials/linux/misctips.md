---
title: Random Tips
---

This page contains random niche tips that I feel should be written somewhere but don't want to make a dedicated turotial for


### Fixing "GPU MEMORY FULL" warning on Davinci Resolve Studio when launching with a Nvidia MX130 GPU on Wayland Gnome NixOS Linux

This took me a while and I am still not sure why it works, but as described in [this](https://discourse.nixos.org/t/davinci-resolve-studio-gpu-memory-full/73650) post, launching the application with these parameters work.  

```env __NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia```

to make this a permanent fix (Albiet not exactly in this nixOS spirit). I installed the gnome [edit-desktop-files](https://search.nixos.org/packages?channel=unstable&include_modular_service_options=1&include_nixos_options=1&query=edit-desktop-files&show=gnomeExtensions.edit-desktop-files) package and used that to conveniently edit the desktop entry so exec reads:

```Exec=env __NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia davinci-resolve-studio```

saving to ```.local/share/applications/```

Now instead of GPU memory full warning being given to me at startup, it is given to me ever so slightly later when I actually try to do something, because at the end of the day, my GPU is an MX130 and 2GB is F all to Davinci Resolve Studio my beloved.

no idea how permanent this fix will be, but  if I remember to update this solution I will.