# Install Zsh in a WSL

## Windows Side

### Install Powerhsell

https://docs.microsoft.com/en-us/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-6

### Install PowerLines fonts

```
git clone https://github.com/powerline/fonts
cd fonts
.\install.ps1
```

### Check presence of WSL in Regedit

Checking if the Console is already registred :
```
if($(Get-ChildItem "HKCU:\Console\*openSUSE*" | Measure-Object).Count -ge 1) 
{
    Write-Host "GOOD ! The console is already registered"
}
else
{
    Write-Host "WARNING ! The specifed app is not registered in the Registry, please edit, for example the font size, in order to force it to persist in the Registry."
}
```

### Update Font pallette for specific WSL

In a powershell :

```
Get-ChildItem "HKCU:\Console\*openSUSE*" | ForEach-Object {
    Set-ItemProperty -Path Registry::$($_.Name) -Name ColorTable00 -Value 3549952
    Set-ItemProperty -Path Registry::$($_.Name) -Name ColorTable01 -Value 9868419
    Set-ItemProperty -Path Registry::$($_.Name) -Name ColorTable02 -Value 7695960
    Set-ItemProperty -Path Registry::$($_.Name) -Name ColorTable03 -Value 10592659
    Set-ItemProperty -Path Registry::$($_.Name) -Name ColorTable04 -Value 1461195
    Set-ItemProperty -Path Registry::$($_.Name) -Name ColorTable05 -Value 12874092
    Set-ItemProperty -Path Registry::$($_.Name) -Name ColorTable06 -Value 8616805
    Set-ItemProperty -Path Registry::$($_.Name) -Name ColorTable07 -Value 14018798
    Set-ItemProperty -Path Registry::$($_.Name) -Name ColorTable08 -Value 4339207
    Set-ItemProperty -Path Registry::$($_.Name) -Name ColorTable09 -Value 13798182
    Set-ItemProperty -Path Registry::$($_.Name) -Name ColorTable10 -Value 39301
    Set-ItemProperty -Path Registry::$($_.Name) -Name ColorTable11 -Value 10002730
    Set-ItemProperty -Path Registry::$($_.Name) -Name ColorTable12 -Value 3093212
    Set-ItemProperty -Path Registry::$($_.Name) -Name ColorTable13 -Value 8533715
    Set-ItemProperty -Path Registry::$($_.Name) -Name ColorTable14 -Value 35253
    Set-ItemProperty -Path Registry::$($_.Name) -Name ColorTable15 -Value 14939901
}
```

## Wsl Side

### Solarized for Vim
The readme is plained fucked up

```
cd ~
curl https://raw.githubusercontent.com/altercation/solarized/master/vim-colors-solarized/colors/solarized.vim --create-dirs --output ~/.vim/colors/solarized.vim

md ~/.vim/config
touch ~/.vim/config/colors.vim
echo syntax enable>> ~/.vim/config/colors.vim
echo set t_Co=256>> ~/.vim/config/colors.vim
echo set background=dark>> ~/.vim/config/colors.vim

touch ~/.vimrc
echo source ~/.vim/config/colors.vim>> ~/.vimrc
set number>> ~/.vimrc
```

### install Oh My Zsh

Follow instruction here 
https://github.com/robbyrussell/oh-my-zsh

Or 
```
sudo zypper update
sudo zypper install zsh
sudo zypper install git
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

```

### change theme of OhMyZsh

https://github.com/robbyrussell/oh-my-zsh/wiki/Themes

For example for `agnoster` :
`vim ~/.zshrc`
change to `ZSH_THEME="agnoster"`

```
curl https://raw.githubusercontent.com/seebi/dircolors-solarized/master/dircolors.256dark --output ~/.dircolors.256dark
echo eval \`dircolors ~/.dircolors.256dark\`>>~/.zshrc
source ~/.zshrc
```