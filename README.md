# Download_through_script
Download any thing through URL in Python script
<pre>
from tqdm import tqdm
import requests

chunk_size = 1024

url = 'http://download.tensorflow.org/example_images/flower_photos.tgz'    //YOUR URL
r = requests.get(url, stream = True)

size = int(r.headers['content-length'])
filename = url.split('/')[-1]

with open(filename, 'wb') as f:
    for data in tqdm(iterable = r.iter_content(chunk_size = chunk_size),
                     total = size/chunk_size, unit = 'KB'):
        f.write(data)


print("Download complete!")</pre>
