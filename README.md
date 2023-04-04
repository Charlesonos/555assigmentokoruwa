# 555assigmentokoruwa
555 assigment


import hashlib
import os
def compute_top_hash(files):
    top_hash = hashlib.sha1() #Using sha1
    for file in files:
        if os.path.isfile(file):  # Only process files, not directories
            with open(file, "rb") as f:
                while True:
                    chunk = f.read(4096)
                    if not chunk:
                        break
                    top_hash.update(chunk)
    return top_hash.hexdigest()
.# Example of using this function
files = os.listdir(".") # list all Pathnames of files in the current directory
top_hash = compute_top_hash(files)
print("Top Hash:", top_hash)

.# If we Modify one or more files the hash value will change.
with open("L1.txt", "a") as f:
    f.write("Adding more data to L1.txt file")

modified_top_hash = compute_top_hash(files)
print("Modified Top Hash:", modified_top_hash)

if top_hash != modified_top_hash:
    print("Top Hash does not match when one or more files are modified")
else:
    print("Top Hash matches when files are not modified")

