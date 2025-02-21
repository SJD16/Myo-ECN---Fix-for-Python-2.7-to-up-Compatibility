# Myo-ECN---Fix-for-Python-2.7-to-up-Compatibility

This repository contains a fix for the streaming.py example from the smetanadvorak/myo_ecn repository. The issue arises due to a deprecated syntax in newer versions of Python (2.7 and above) in the MultichannelPlot.py file.

##Issue Description
The streaming.py script uses a MultichannelPlot class for visualizing EMG data from the MYO armband. However, the following line in MultichannelPlot.py causes an error in Python 2.7 and above:
```bash
self.axes = [self.fig.add_subplot(str(self.nchan) + '1' + str(i+1)) for i in range(self.nchan)]
```
I belive this line uses an outdated syntax for creating subplots in Matplotlib, which is no longer supported in newer versions of Python.

##Fix
To resolve this issue, replace the problematic line in MultichannelPlot.py with the following updated syntax:

```bash
self.axes = [self.fig.add_subplot((self.nchan), 1, i) for i in range(1, (self.nchan))]
```
This change ensures compatibility with newer versions of Python and Matplotlib.
## Steps to Apply the Fix
 ### 1. Locate the MultichannelPlot.py file in the repository.
 ### 2. Open the file and find the following line (around line 11 or 12):
```bash
  self.axes = [self.fig.add_subplot(str(self.nchan) + '1' + str(i+1)) for i in range(self.nchan)]
```
 ### 3. Replace the line with the updated syntax:
 ```bash
 self.axes = [self.fig.add_subplot((self.nchan), 1, i) for i in range(1, (self.nchan))]
```
 ### 4. Save the file and re-run the streaming.py script.
 
 ## Download Fixed File
 If you don’t want to manually edit the file, you can download the fixed MultichannelPlot.py from this repository. Simply replace the original file with the one provided here.

 ## Example Usage
 After applying the fix, you can run the streaming.py script without issues:
  ```bash
# Setup multichannel plotter for visualization:
plotter = MultichannelPlot(nchan=8, xlen=512)  # Number of EMG channels in MYO armband is 8
```
This will now work correctly in Python 2.7 and above.

# Credits

    Original repository: smetanadvorak/myo_ecn
    Fix contributed by: [SJD16]

## License

This project is licensed under the same terms as the original repository. Please refer to the original repository for licensing details.

## Contributing
If you encounter any other issues or have suggestions for improvement, feel free to open an issue or submit a pull request.
