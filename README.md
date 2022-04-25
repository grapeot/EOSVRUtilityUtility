# EOS VR Utility Utility

This is a small utility to make Canon EOS VR Utility easier to use.

When using the great EOS VR system, I got two pain points.
The first is the software doesn't accept RAW files, even for images.
We have to use the output jpg files directly from the body, instead of the more flexible and capable RAW files.
The second is the entire EOS VR Utility software is implemented with blocking behaviors.
That is, when clicking anything such as selecting a file, the UI will completely freeze while doing (usually time consuming) computation.
This is really annoying when one has tens or hundreds of photos to process.

This utility doesn't solve the two issues directly, but greatly alleviate the issues.
For the first one, it allows the EOS VR Utility to recognize the derived jpgs from RAW files.
And for the second one, it enabled "Horizontal Correction" by default, so we don't need to click into each image and wait for two minutes to click the "Hozirontal Correction" button.

## Usage

This is a python script.
So please first install python 3, and also make sure `exittool` is installed and put into the system PATH.
Assuming the jpg files derived from the RAW files are stored in the folder `./jpgs`, and the original jpg files right from the camera are stored in the folder `./raw_jpgs`, then we can execute the following command:

```
python ./enableJpgs.py --jpgdir ./jpgs --rawdir ./raw_jpgs
```

This will write corresponding xml files to `./jpgs`, and patch the jpg files so the EOS VR Utility could recognize them.

## My Workflow

I also share my workflow of processing VR media here.
After shooting using the (great) R5 and VR lens, I have a bunch of RAW files, and corresponding jpg files.
I first use CaptureOne (or Lightroom) to pick the good pictures from the RAW files, edit them in the circular form, and export to high quality jpg.
Then this tool is used to enable EOS VR Utility to recognize them.
In the EOS VR Utility UI, a multiple selection by holding the Shift key and export would convert them to the square form.
Then I usually use Topaz Gigapixel to enlarge them to 16k, which solves another pain point of insufficient resolution.
It sounds counter-intuitive because R5 is already an 8k camrea.
But the 8k is for the photos of both eyes.
So each eye only has 4k pixels horizontally.
And it needs to be further divided into 180 degrees.
So the resolution is actually not that high after alll the division.
It turned out such kind of artificial resolution boost is pretty effective on a Oculus Quest 2.