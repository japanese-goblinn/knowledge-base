- e.g. `1.0.0 (0)` where `1.0.0` - version and `(0)` - build number
- Two approaches to use build numbers 
	- TF - [Test Flight](Test%20Flight.md)
	- R - release
	- *Always increment*
		- `1.0.0 (1)` - TF
		- `1.0.0 (2)` - TF + R
		- `1.0.1 (3)` - TF
		- `1.0.1 (4)` - R
		- ...
	- *Build version is individual for every version* 
		- `1.0.0 (0)` - TF
		- `1.0.0 (1)` - TF + R
		- `1.0.1 (0)` - TF
		- `1.0.1 (1)` - TF
		- `1.0.1 (2)` - TF + R
		- ...