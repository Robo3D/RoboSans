# RoboSans

RoboSans is derived from [Noto Sans](https://github.com/googlei18n/noto-fonts)
and [Noto Sans CJK](https://github.com/googlei18n/noto-cjk). Noto Sans CJK supports
Chinese, Japanese, and Korean characters. We needed a centralized font to avoid
switching to another font to correctly display certain characters for a supported
language. Using Noto Sans CJK doesn’t have english and latin characters that
have a similar style to our existing font, but Noto Sans does. Combining Noto Sans
and Noto Sans CJK gives us a similar look to our current one while being consistent
with supporting other languages. Making a single font for all languages
to reference will be consistent and maintainable. Both Noto Sans and Noto Sans CJK
are licensed under Open Font License Version 1.1.

RoboSans has two different fonts: RoboSans-Regular and RoboSans-Bold.

RoboSans-Regular uses NotoSans-SemiCondensed, for english and latin
characters, and NotoSansSC-Regular, for simplified chinese characters.

RoboSans-Bold uses NotoSans-Semi Condensed Bold, for english and latin
characters, and NotoSansSC for simplified chinese characters. RoboSans will be
updated with languages that we will support.

### Creation

RoboSans was created using FontForge. FontForge cannot view all of the characters
in Noto Sans CJK by default due to the amount of code points used. The CJK fonts
needs to be prepared for FontForge to view correctly.
[cjk-multi-fix.py](https://github.com/fontforge/fontforge/issues/1534#issuecomment-348835384)
was used to modify the font to view correctly in FontForge. Modifications to
cjk-multi-fix.py was made so it can be ran through python instead of FontForge
script by importing sys.

# Setup
## Environment
### Mac OS (Using Homebrew)
Install dependencies using Homebrew

```
brew update
brew install cask xquartz
brew install freetype
brew install fontforge
brew install cask fontforge
```

Install dependencies using Python

```
pip install freetype-py
```

## Merging Font
Make Noto CJK font compatible with FontForge using cjk-multi-fix.py.
Simplified Chinese is used in this setup.

```
python cjk-multi-fix.py NotoSansSC-Regular.otf NotoSansSC-Regular-fix.otf
```

- Open FontForge
- Open NotoSansSC-Regular-fix.oft in FontForge
- Open NotoSans-SemiCondensed.ttf in FontForge
- Using NotoSans-SemiCondensed.ttf, go to Elements->Merge Fonts…
- NotoSansSC-Regular should be selected in the dropdown menu
- Cross-font kerning should be checked
- Click OK
- Go to File->Generate Fonts…
- Name the new font and click Generate
