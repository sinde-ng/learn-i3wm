<center>
  <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/2/27/I3_window_manager_logo.svg/2141px-I3_window_manager_logo.svg.png" width="80px" height="80px">
  <h2>Belajar Configurasi i3 Window Manager</h2>
</center>

<br>

<a href="https://i3wm.org/docs/userguide.html">visit official i3wm</a>

<br>

<h4>Apa itu i3wm ???</h4>
`
    i3 merupakan sebuah manager jendela yang dirancang untuk x11 (sistem grafis pada sistem operasi unix). Untuk window manager sendiri merupakan sebuah sistem yang mengontol juga menampilkan sebuah tab maupun jendela.
    Kebanyakan user linux tidak asing dengan window manager/manajer jendela yang bernama i3. Karena i3 sangat cocok bagi seorang pemula dengan konfigurasinya yang jauh lebih mudah daripada window manager lainnya.
`
<br>

<h4>Lokasi File Config</h4>
  ```
    $HOME/.config/i3/config
  ```
<br>

<h4>Menentukan Modifier Key</h4>
  ```
    Saya sendiri dan mungkin kebanyakan orang juga menggunakan Mod4 atau tombol windows
      set $mod Mod4
  ```
  
<br>

<h4>Setting Keybinding</h4>
  <h5>Terminal</h5>
    ```
      bindsym $mod+Return exec --no-startup-id st
      Return: merupakan tombol enter
    ```
  <h5>Menutup Aplikasi</h5>
  ```
    bindsym $mod+Shift+q kill
  ```
  <h5>Launcher Apps (Mencari Aplikasi)</h5>
    ```
      bindsym $mod exec --no-startup-id j4-dmenu-desktop --dmenu='rofi -dmenu -lines 6 -width 400 -i -sort -p RUN'
    ```
   <h5>Window Container</h5>
    ```
        1. Berpindah fokus (menggunakan arrow keyboard)
            bindsym $mod+Up focus up
            bindsym $mod+Down focus down
            bindsym $mod+Left focus left
            bindsym $mod+Right focus right
        2. Memindahkan Fokus Container
            a. Versi Lambat
              bindsym $mod+j move up 1px 
              bindsym $mod+k move down 1px
              bindsym $mod+l move left 1px
              bindsym $mod+; move right 1px
            b. Versi Cepat
              bindsym $mod+Shift+Up move up 1px 
              bindsym $mod+Shift+Down move down 1px
              bindsym $mod+Shift+Left move left 1px
              bindsym $mod+Shift+Right move right 1px
        3. Mengganti Orientasi Container
            a. Orientasi Bawaan
              default_orientation vertical
            b. Vertikal
              bindsym $mod+v split v
            c. Horizontal
              bindsym $mod+h split h
        4. Fullscreen 
            bindsym $mod+f fullscreen toogle
        5. Layout Container
            workspace_layout default
        6. Membuat Container menjadi Tipe Floating
            bindsym $mod+Shift+space floating toggle border none
        7. Pindah Focus pada Container Floating
            bindsym $mod+space focus mode_toggle
        8. Parent Container
            bindsym $mod+a focus parent
        9. Child Focus
            bindsym $mod+Shift+a focus child
        10. Scratchpad (Solusi jika ingin menggunakan app lain tanpa pindah workspace)
            a. Membuat Container menjadi Scratchpad
              bindsym $mod+Shift+minus move scratchpad
            b. Menyembunyikan scratchpad
              bindsym $mod+minus scratchpad show 
        11. Sticky Container (Container to Front/Top)
            bindsym $mod+Shift+plus sticky toggle
        12. Binding Mode (Maximize/Minimize)
            a. Activated Binding Mode
              bindsym $mod+r mode "resize"
            b. Mode Normal (tap enter or escape)
              bindsym Return mode "default"
              bindsym Escape mode "default"
            c. Keyboard Shortcut
              bindsym j resize shrink width  1 px
              bindsym k resize grow   height 1 px
              bindsym l resize shrink height 1 px
              bindsym ; resize grow   width  1 px
            d. Arrow Keyboard
              bindsym Left  resize shrink width  1 px or 1 ppt
              bindsym Down  resize grow   height 1 px or 1 ppt
              bindsym Up    resize shrink height 1 px or 1 ppt
              bindsym Right resize grow   width  1 px or 1 ppt
        13. Container Border
            a. Keyboard Shortcut
              bindsym $mod+Shift+t border normal 0
              bindsym $mod+t       border normal 1
              bindsym $mod+Shift+y border pixel  1
              bindsym $mod+y       border none
       14. Create Empty Container
            bindsym $mod+o open
       15. Berpindah Workspace
            a. Cara 1 
              bindsym $mod+1 workspace $workspace1
              bindsym $mod+2 workspace $workspace2
              bindsym $mod+3 workspace $workspace3
              bindsym $mod+4 workspace $workspace4
              bindsym $mod+5 workspace $workspace5
              bindsym $mod+6 workspace $workspace6
              bindsym $mod+7 workspace $workspace7
              bindsym $mod+8 workspace $workspace8
              bindsym $mod+9 workspace $workspace9
              bindsym $mod+0 workspace $workspace10
            b. Cara 2
              bindsym $mod+Tab exec --no-startup-id j4-dmenu-desktop --dmenu="rofi -show window -lines 10 -width 500 -display-window 'WORKSPACE'"
        16 Reload
            bindsym $mod+Shift+c reload
        17. Restart
            bindsym $mod+Shift+c reload
    ```

<br>
 
<h4>Setting Window</h4> 
  <h5>Container Border</h5>
    ```
      new_windows none
      new_float none
    ```

<br>

        
      # Default Floating Container
        for_window [class="Gkamus"]                           floating enable border normal 1
        for_window [class="Gnome-power-statistics"]           floating enable border normal 1
        for_window [class="Modem-manager-gui"]                floating enable border normal 1
        for_window [class="Gnome-system-monitor"]             floating enable border normal 1
        for_window [class="Nm-connection-editor"]             floating enable border normal 1
        for_window [class="zoom" title="Zoom - Free Account"] floating enable border pixel  1 move right 470px,move down 0px
        for_window [class="st-256color" title="ncpamixer"]    floating enable border normal 1 resize set 500 600,move right 90px,move up 80px
        for_window [class="scrcpy" title="Mi-4c"]             floating enable border none     move right 460px,move down 0px
        # Default Floating
          for_window [class="pavucontrol-qt"]                    floating disable
          
          
      # Window Color
        # Variable
        set $bg-color               #000000
        set $text-color             #000000
        set $border-color           #000000
        set $inactive-bg-color      #000000
        set $inactive-text-color    #000000
        set $urgent-bg-color        #000000
        set $urgent-text-color      #000000
        set $indicator              #000000
        
        # Opetion Name              # Border              # Background          # Text                  # Indicator
        client.focused              $bg-color             $bg-color             $text-color             $indicator
        client.unfocused            $inactive-bg-color    $inactive-bg-color    $inactive-text-color    $indicator
        client.focused.inactive     $inactive-bg-color    $inactive-bg-color    $inactive-text-color    $indicator
        client.urgent               $urgent-bg-color      $urgent-bg-color      $urgent-text-color      $indicator
        
        
# Workspace
  set $workspace1  "1"
  set $workspace2  "2"
  set $workspace3  "3"
  set $workspace4  "4"
  set $workspace5  "5"
  set $workspace6  "6"
  set $workspace7  "7"
  set $workspace8  "8"
  set $workspace9  "9"
  set $workspace10 "10"
        
# Gaps Container
  gaps inner 0
  gaps outer 5px
  smart_gaps on
  
# Clipboard
  # Installation (terminal)
    $ cd your_directory
    $ git clone https://github.com/cdown/clipmenu.git
    $ cd clipmenu
    $ sudo ln -sf $HOME/your_directory/clipmenu/clipdel /usr/bin/clipdel
    $ sudo ln -sf $HOME/your_directory/clipmenu/clipmenu /usr/bin/clipmenu
    $ sudo ln -sf $HOME/your_directory/clipmenu/clipmenud /usr/bin/clipmenud
    # Check for Installation
      $ ll /usr/bin | grep -E 'clipdel|clipmenu|clipmenud'
  # Configuration (config file)
    exec --no-startup-id clipmenud
    # Service Systemd (terminal)
      $ sudo systemctl enable clipmenud.service
      $ sudo systemctl start clipmenud.service
    # Definition
      $ nano ~/.profile
        PASTE THIS :
          export CM_LAUNCHER=rofi-clipmenu
          export CM_DIR=/tmp
      $ sudo nano ~/.local/bin/rofi-clipmenu
        PASTE THIS : rofi -dmenu -p 'CLIPBOARD' -lines 8 -width 500
      $ chmod +x ~/.local/bin/rofi-clipmenu
    # Keyboard Shortcut 
      bindsym $mod+p exec --no-startup-id clipmenu
      # Remove All Clipboard
      bindsym $mod+Shift+p exec --no-startup-id clipdel -d '.' 
      
# Polkit
  exec --no-startup-id /usr/bin/lxpolkit
      
# Window Composite 
  exec --no-startup-id compton --config ~/.config/compton/compton.conf
  
# Notification
  exec --no-startup-id dunst -config ~/.config/dunst/dunstrc
      
# Polybar
  exec_always --no-startup-id ~/.config/polybar/launch.sh
      
# System Session (Logout, Restart and Shutdown)
  bindsym $mod+Shift+End exec --no-startup-id ~/.local/bin/rofi-power "i3-msg exit"
  
# Volume Control
  bindsym XF86AudioRaiseVolume exec --no-startup-id pamixer --increase 2
  bindsym XF86AudioLowerVolume exec --no-startup-id pamixer --decrease 2
  bindsym XF86AudioMute        exec --no-startup-id pamixer --toggle-mute
  bindsym XF86AudioMicMute     exec --no-startup-id pactl   set-source-mute 1 toggle
  
# Audio Mixer
  bindsym $mod+F3 exec --no-startup-id pavucontrol
  
# Brightness Control
  bindsym XF86MonBrightnessUp   exec --no-startup-id xbacklight -inc 2
  bindsym XF86MonBrightnessDown exec --no-startup-id xbacklight -dec 2
  
# Arandr (Dual Monitor)  
  bindsym $mod+F7 exec --no-startup-id arandr
  
# Network Manager
  # Installation
    $ mkdir -p ~/.config/networkmanager-dmenu
    $ git clone https://github.com/firecat53/networkmanager-dmenu.git ~/.config/networkmanager-dmenu
    $ cd ~/.config/networkmanager-dmenu
    $ nano ~/.config/rofi/config.ini
      PASTE THIS :
        [dmenu]
        fn = Fantasque Sans Mono
        dmenu_command = /usr/bin/rofi -width 25
        # # Note that dmenu_command can contain arguments as well like `rofi -width 30`
# # Rofi and dmenu are set to case insensitive by default `-i`
# l = number of lines to display, defaults to number of total network options
# fn = font string
# nb = normal background (name, #RGB, or #RRGGBB)
# nf = normal foreground
# sb = selected background
# sf = selected foreground
# b =  (just set to empty value and menu will appear at the bottom
# m = number of monitor to display on
# p = Custom Prompt for the networks menu
p = NETWORKS
# pinentry = Pinentry command
# rofi_highlight = &lt;True or False&gt; # (Default: False) use rofi highlighting instead of '**'

# # override normal foreground and background colors (dmenu) or use the
# # -password option (rofi) to obscure passphrase entry
# [dmenu_passphrase]
# nf = #222222
# nb = #222222
# rofi_obscure = True

      [editor]
      terminal = st
      gui_if_available = True
      # terminal = &lt;name of terminal program&gt;
      # gui_if_available = &lt;True or False&gt;
  # Configuration
    bindsym $mod+F8 exec --no-startup-id networkmanager_dmenu
  
# Autostart Application
  exec        <name_program>
  exec_always <name_program>

  exec          --no-startup-id  <name_program>
  exec_always   --no-startup-id  <name_program>
      
# Setting Wallpaper
  # write on your terminal (i use debian)
    $ sudo apt install feh
  # configuration on config file
    exec_always --no-startup-id feh --bg-fill -Z ~/..your-directory.png
          
# LockScreen
  bindsym $mod+Shift+x exec --no-startup-id /usr/bin/lock-dark
  exec_always --no-startup-id xautolock -time 15 -locker "/usr/bin/lock-dark" && echo mem ? /sys/power/state     
        
# Konfigurasi Font
  font pango:Fantasque Sans Mono 10
