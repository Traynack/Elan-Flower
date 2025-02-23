<div align = center>
    <a href="https://discord.gg/AYbJ9MJez7">
        <img alt="Dynamic JSON Badge" src="https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fdiscordapp.com%2Fapi%2Finvites%2FmT5YqjaJFh%3Fwith_counts%3Dtrue&query=%24.approximate_member_count&suffix=%20members&style=for-the-badge&logo=discord&logoSize=auto&label=The%20HyDe%20Project&labelColor=ebbcba&color=c79bf0">  
    </a>
</div>
<div align = center><img src="https://raw.githubusercontent.com/prasanthrangan/hyprdots/main/Source/assets/hyde_banner.png"><br><br></div>

# Élan Flower
A customized theme for HyDE Hyprland

This is a theme that I designed for myself for use with multiple wallpapers of varying colors, so its installation/removal is a little unorthadox, and conflicts with HyDE's default Wallbash generation scripts, meaning it'll probably break after HyDE updates. With that said though, I'm sure that there's a much better way of doing what is being done here, and if anyone knows of a better way of doing this, please let me know.

# Installation
1. Install [HyDE](https://hydeproject.pages.dev/guides/cli/#installation) using the CLI tool. (You can do it without Hyde-cli and install HyDE manually, but you'll need to also manually add the themes below instead of using Hyde-cli.)
2. Run the following two commands to install both the light and dark themes into your HyDE installation. (Or just one, depending on your preference)

   ```sh
   Hyde theme import "Élan Flower Light" https://github.com/Traynack/HyDE-Elan-Light
   ```
   
   ```sh
   Hyde theme import "Élan Flower Dark" https://github.com/Traynack/HyDE-Elan-Dark
   ```
3. Use the keybinds `SUPER + SHIFT + T` to change the theme to one of the two freshly installed themes, `SUPER + SHIFT + R` to set Wallbash mode to `auto`, and `SUPER + ALT + UP/DOWN` to change the waybar style to your liking.

> [!IMPORTANT]
> This theme relies on Wallbash and HyDE to make a custom GTK theme and colors every time you switch the wallpaper, which can be done with `SUPER + SHIFT + W` after you add your own in `$HOME/.config/hyde/themes/Élan Flower (Light/Dark)/wallpapers`. This theme is **not** designed to be used with the `.theme` files (aside from `hypr.theme`), and because of that, some of the things that can usually be changed with `.theme` files need to be changed manually. You can do all or none of them, I'm certainly not your system admistrator. 😅

## Kitty font change
(Ususally controlled with `.theme` file) 

Add the following 2 lines:
```
font_family     MonofurNerdFontMono
font_size     12
```
to the end of `$HOME/.config/kitty/kitty.conf`.

## Fastfetch
### Fastfetch on Kitty startup
Open up `$HOME/.hyde.zshrc` and comment out the line 
```
pokego --no-title -r 1,3,6
```
and uncomment
```
# fastfetch.sh
```
### Default fastfetch changes
* Remove `aisaka.icon`, `loli.icon`, `pochita.icon`, and `ryuzaki.icon` from `$HOME/.config/fastfetch/logo/`
* Replace the `config.jsonc` file in `$HOME/.config/fastfetch/` with the one found in this repository.

## Waybar font size fix
> [!IMPORTANT]
> This is the only thing that should conflict with HyDE when it updates, as it changes files that aren't meant to be changed. If there's a way to change the Waybar font size manually without needing to edit the `wbarstylegen.sh`, let me know!

* Open up `$HOME/.local/lib/hyde/wbarstylegen.sh`
* Comment out
  
  ```sh
  export s_fontpx=$((b_height * 34 / 100)) # font size 34% of height
  ```
  
  on line 39, and add
  
  ```sh
  export s_fontpx=$((12)) # Changes made by the Élan Flower theme.
  ```
  
  on a new line, idealy on line 39 or 40. It should look something like this when you're done:
  
  ```sh
  38 export w_padact=$((b_height * 40 / 100)) # workspace active padding 40% of height
  39 export s_fontpx=$((12)) # Changes made by the Élan Flower theme.
  40 # export s_fontpx=$((b_height * 34 / 100)) # font size 34% of height
  ```
* Make sure to reload the waybar so this script runs, this can be done by just changing the theme or wallpaper after you save the file. This should make it so that the font used by this theme is roughly the same size as the default one provided by HyDE. If it's not, you can change the ``12`` to a font size more consistant with your display.

## Firefox navigation bar font change
1. Go to the `about:config` page in Firefox.

> [!IMPORTANT]
> Heed the warning about changing the default config. All that will be done is toggling an option to enable `userChrome.css` and `userContent.css` in the `chrome` folder of your Firefox profile. See [here](https://support.mozilla.org/si/questions/1335097) for more information.

2. Search for `toolkit.legacyUserProfileCustomizations.stylesheets` and change it to `true`.
3. Go to `about:profiles`
4. Look for the profile that says 'This is the profile in use and cannot be deleted.' and open the root directory of it.
5. If it doesn't already exist, make a new folder called `chrome` in the directory that just opened up, and then inside of it make a file named `userChrome.css` with the following content:
```css
#navigator-toolbox { font-family:MonofurNerdFont !important }
```
6. Save the new file and restart Firefox.

# Resources used
* [The HyDE Project](https://github.com/HyDE-Project)
* Default Élan Flower Light wallpaper: Rain and Mila by [papaya](https://bsky.app/profile/papaira.bsky.social/post/3lirhjvisu22u)
* Default Élan Flower Dark wallpaper: Rainy Drive CG from [Twofold](https://store.steampowered.com/app/1749770/Twofold/)
* Icon Theme: [Zafiro Icons](https://www.gnome-look.org/p/1209330) by zayronxio
* Font: [Monofur](https://www.nerdfonts.com/font-downloads)
* Music player featured in screenshots: [Harmonoid](https://github.com/harmonoid/harmonoid) by alexmercerind
  
Most of the screenshots in the [r/unixporn](https://www.reddit.com/r/unixporn/comments/1iw3wiq/hyprland_customized_hyde_i_cant_choose_just_one/) post are avaliable on Studio Élan's [patreon](https://www.patreon.com/vnstudioelan). If you like them, show the team over there some love. ❤

The characters featured in them are [Please Be Happy](https://store.steampowered.com/app/844670/Please_Be_Happy/)'s main cast (Miho, Aspen, and Juliet), [Twofold](https://store.steampowered.com/app/1749770/Twofold/)'s main cast (Olive, Caprice, Millie, and Hayley) and [Upwards, Rain!](https://vnstudioelan.itch.io/upwards-rain)'s main characters, Rain and Mila.
