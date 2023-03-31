# Setting up Kivy on Mac

Kivy is a Python framework for building cross-platform GUI applications. This README provides instructions for setting up Kivy on a Mac using a bash script to automate the installation process.

## Prerequisites

Before installing Kivy, make sure you have the following prerequisites installed:

- Homebrew
- Python 3

If you don't have Homebrew installed, you can install it by running the following command in your terminal:
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

To install Python 3 using Homebrew, run the following command:
```
brew install python
```

## Installation

To automate the installation of Kivy and its dependencies, use the following bash script:
```
#!/bin/bash

# Check if Homebrew is installed
if test ! $(which brew); then
    echo "Installing Homebrew..."
    /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
fi

# Update Homebrew and install dependencies
brew update
brew install pkg-config sdl2 sdl2_image sdl2_ttf sdl2_mixer gstreamer

# Install Python 3 and pip
brew install python

# Install Kivy
pip3 install kivy
```

To use this script, save it to a file (e.g. kivy_setup.sh) and make it executable by running the command:
```
chmod +x kivy_setup.sh
```

Then, run the script with the command:

```
./kivy_setup.sh
```

This will install the dependencies for Kivy and install Kivy itself using pip3.

After the script completes, you can test that Kivy is installed correctly by creating a file named main.py with the following code:
```
import kivy

from kivy.app import App
from kivy.uix.label import Label


class MyApp(App):

    def build(self):
        return Label(text='Hello, Kivy!')


if __name__ == '__main__':
    MyApp().run()
```

Save the file and run it with the command:

```
python main.py
```

This should launch a Kivy window with the text "Hello, Kivy!" displayed in the center. If you see this, then Kivy is installed correctly and you're ready to start building GUI applications with Python!
