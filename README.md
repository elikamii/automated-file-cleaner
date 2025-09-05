import os
import time

def clean_old_files(directory, days):
    """
    Deletes files in a directory that are older than the specified number of days.
    """
    now = time.time()
    for filename in os.listdir(directory):
        filepath = os.path.join(directory, filename)
        if os.stat(filepath).st_mtime < now - days * 86400:
            if os.path.isfile(filepath):
                print(f"Deleting {filepath}...")
                os.remove(filepath)

# Example usage:
# Specify the directory and the number of days.
# clean_old_files("/path/to/your/directory", 30)
