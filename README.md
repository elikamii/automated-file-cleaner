import os
import time

def clean_old_files(directory, days):
    """
    Deletes files in a directory that are older than the specified number of days.
    """
import os
import time

def clean_old_files(directory, days, file_extensions=None):
    """
    Deletes files in a directory that are older than the specified number of days.
    Optionally filters by a list of file extensions.
    """
    now = time.time()
    for filename in os.listdir(directory):
        filepath = os.path.join(directory, filename)
        
        # Check if the file matches the specified extensions
        if file_extensions and not filename.endswith(tuple(file_extensions)):
            continue

        if os.stat(filepath).st_mtime < now - days * 86400:
            if os.path.isfile(filepath):
                print(f"Deleting {filepath}...")
                os.remove(filepath)

# Example usage:
# To delete all files older than 30 days:
# clean_old_files("/path/to/your/directory", 30)
#
# To delete only .log and .tmp files older than 7 days:
# clean_old_files("/path/to/your/directory", 7, file_extensions=['.log', '.tmp'])    for filename in os.listdir(directory):
        filepath = os.path.join(directory, filename)
        if os.stat(filepath).st_mtime < now - days * 86400:
            if os.path.isfile(filepath):
                print(f"Deleting {filepath}...")
                os.remove(filepath)

# Example usage:
# Specify the directory and the number of days.
# clean_old_files("/path/to/your/directory", 30)
