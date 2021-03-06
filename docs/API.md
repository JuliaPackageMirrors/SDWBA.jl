# SDWBA

## Exported

---

<a id="method__freq_spectrum.1" class="lexicon_definition"></a>
#### freq_spectrum(s::SDWBA.Scatterer{T},  freq1,  freq2,  sound_speed) [¶](#method__freq_spectrum.1)
Calculate backscatter over a range of frequencies.  The insonifying sound comes
from above (i.e., traveling in the -z direction).

#### Parameters
- `s` : Scatterer object
- `freq1`, `freq2` : Endpoints of the angle range to calculate.
- `sound_speed` : Sound speed in the surrounding medium
- `n` : Number of frequencies to calculate; defaults to 100

Returns: A dictionary containing elements "freqs", "sigma_bs", and "TS",
	each a length-n vector.


*source:*
[SDWBA/src/Scatterer.jl:275](https://github.com/ElOceanografo/SDWBA.jl/tree/58159dc1cd2fa7416e74887232848ebaba820633/src/Scatterer.jl#L275)

---

<a id="method__freq_spectrum.2" class="lexicon_definition"></a>
#### freq_spectrum(s::SDWBA.Scatterer{T},  freq1,  freq2,  sound_speed,  n) [¶](#method__freq_spectrum.2)
Calculate backscatter over a range of frequencies.  The insonifying sound comes
from above (i.e., traveling in the -z direction).

#### Parameters
- `s` : Scatterer object
- `freq1`, `freq2` : Endpoints of the angle range to calculate.
- `sound_speed` : Sound speed in the surrounding medium
- `n` : Number of frequencies to calculate; defaults to 100

Returns: A dictionary containing elements "freqs", "sigma_bs", and "TS",
	each a length-n vector.


*source:*
[SDWBA/src/Scatterer.jl:275](https://github.com/ElOceanografo/SDWBA.jl/tree/58159dc1cd2fa7416e74887232848ebaba820633/src/Scatterer.jl#L275)

---

<a id="method__from_csv.1" class="lexicon_definition"></a>
#### from_csv(filename) [¶](#method__from_csv.1)
Load a scatterer from a file on disk with comma-separated values.

#### Parameters
- `filename` : String.  Path to the datafile.  This should be a standard .csv file 
with columns for the x, y, and z coordinates of the scatterer's centerline, as well
as the `a`, `h`, and `g` arguments to Scatterer().
- `columns` : Optional dictionary of column names. If the columns do not have the names 
- `x`, `y`, `z`, `h`, and `g`, this must be provided.  The keys are the standard column
names and the values are the actual ones in the file.


*source:*
[SDWBA/src/Scatterer.jl:297](https://github.com/ElOceanografo/SDWBA.jl/tree/58159dc1cd2fa7416e74887232848ebaba820633/src/Scatterer.jl#L297)

---

<a id="method__from_csv.2" class="lexicon_definition"></a>
#### from_csv(filename,  columns) [¶](#method__from_csv.2)
Load a scatterer from a file on disk with comma-separated values.

#### Parameters
- `filename` : String.  Path to the datafile.  This should be a standard .csv file 
with columns for the x, y, and z coordinates of the scatterer's centerline, as well
as the `a`, `h`, and `g` arguments to Scatterer().
- `columns` : Optional dictionary of column names. If the columns do not have the names 
- `x`, `y`, `z`, `h`, and `g`, this must be provided.  The keys are the standard column
names and the values are the actual ones in the file.


*source:*
[SDWBA/src/Scatterer.jl:297](https://github.com/ElOceanografo/SDWBA.jl/tree/58159dc1cd2fa7416e74887232848ebaba820633/src/Scatterer.jl#L297)

---

<a id="method__length.1" class="lexicon_definition"></a>
#### length(s::SDWBA.Scatterer{T}) [¶](#method__length.1)
Return the length of the scatterer (cartesian distance from one end to the other).


*source:*
[SDWBA/src/Scatterer.jl:50](https://github.com/ElOceanografo/SDWBA.jl/tree/58159dc1cd2fa7416e74887232848ebaba820633/src/Scatterer.jl#L50)

---

<a id="method__rescale.1" class="lexicon_definition"></a>
#### rescale(s::SDWBA.Scatterer{T}) [¶](#method__rescale.1)
Scale the scatterer's size (overall or along a particular dimension) by a 
constant factor.

#### Parameters
- `s` : Scatterer object.
- `scale` : Factor by which to grow/shrink the scatterer.
- `radius`, `x`, `y`, `z` : Optional factors, scaling the scatterer's radius
and along each dimension in space. All default to 1.0.

#### Returns
A rescaled scatterer.

#### Details
When making a scatterer larger, it is important to make sure it's body has enough
segments to accurately represent the shape at the frequencies of interest.
Specifically, the ratio L / (N λ), where L is the length of the animal, N is the
number of segments, and λ is the acoustic wavelength, should remain constant, which
may require interpolating new points between the existing ones. See Conti and 
Demer (2006) or Calise and Skaret (2011) for details.


*source:*
[SDWBA/src/Scatterer.jl:75](https://github.com/ElOceanografo/SDWBA.jl/tree/58159dc1cd2fa7416e74887232848ebaba820633/src/Scatterer.jl#L75)

---

<a id="method__resize.1" class="lexicon_definition"></a>
#### resize(s::SDWBA.Scatterer{T},  len) [¶](#method__resize.1)
Resize a scatterer.  This is a convenience wrapper around `rescale`, for the
common situation where you want to change a scatterer to a specific length.
The scatterer's relative proportions are preserved.

#### Parameters
- `s` : Scatterer 
- `len` : Desired length to which the scatterer should be scaled.

#### Returns
A resized scatterer.


*source:*
[SDWBA/src/Scatterer.jl:98](https://github.com/ElOceanografo/SDWBA.jl/tree/58159dc1cd2fa7416e74887232848ebaba820633/src/Scatterer.jl#L98)

---

<a id="method__rotate.1" class="lexicon_definition"></a>
#### rotate(s::SDWBA.Scatterer{T}) [¶](#method__rotate.1)
Rotate the scatterer in space, returning a rotated copy.

#### Parameters
- `roll` : Angle to roll the scatterer, in degrees. Defaults to 0.
- `tilt` : Angle to tilt the scatterer, in degrees. Defaults to 0.
- `yaw` : Angle to yaw the scatterer, in degrees. Defaults to 0.

#### Returns
A Scatterer with the same shape and properties, but a new orientation.

The roll, tilt, and yaw refer to rotations around the x, y, and z axes,
respectively. They are applied in that order.


*source:*
[SDWBA/src/Scatterer.jl:144](https://github.com/ElOceanografo/SDWBA.jl/tree/58159dc1cd2fa7416e74887232848ebaba820633/src/Scatterer.jl#L144)

---

<a id="method__tilt_spectrum.1" class="lexicon_definition"></a>
#### tilt_spectrum(s::SDWBA.Scatterer{T},  angle1,  angle2,  k) [¶](#method__tilt_spectrum.1)
Calculate backscatter over a range of angles.

#### Parameters

- `s` : Scatterer object
- `angle1`, `angle2` : Endpoints of the angle range to calculate.
- `k` : Acoustic wavenumber vector
- `n` : Number of angles to calculate; defaults to 100

#### Returns

A dictionary containing elements "angles", "sigma_bs", and "TS",
each a length-n vector.


*source:*
[SDWBA/src/Scatterer.jl:250](https://github.com/ElOceanografo/SDWBA.jl/tree/58159dc1cd2fa7416e74887232848ebaba820633/src/Scatterer.jl#L250)

---

<a id="method__tilt_spectrum.2" class="lexicon_definition"></a>
#### tilt_spectrum(s::SDWBA.Scatterer{T},  angle1,  angle2,  k,  n) [¶](#method__tilt_spectrum.2)
Calculate backscatter over a range of angles.

#### Parameters

- `s` : Scatterer object
- `angle1`, `angle2` : Endpoints of the angle range to calculate.
- `k` : Acoustic wavenumber vector
- `n` : Number of angles to calculate; defaults to 100

#### Returns

A dictionary containing elements "angles", "sigma_bs", and "TS",
each a length-n vector.


*source:*
[SDWBA/src/Scatterer.jl:250](https://github.com/ElOceanografo/SDWBA.jl/tree/58159dc1cd2fa7416e74887232848ebaba820633/src/Scatterer.jl#L250)

---

<a id="method__to_csv.1" class="lexicon_definition"></a>
#### to_csv(s::SDWBA.Scatterer{T},  filename) [¶](#method__to_csv.1)
Save a scatterer's shape to a file on disk with comma-separated values.

#### Parameters
- `s` : Scatterer object to save.
- `filename` : Where to save it.



*source:*
[SDWBA/src/Scatterer.jl:318](https://github.com/ElOceanografo/SDWBA.jl/tree/58159dc1cd2fa7416e74887232848ebaba820633/src/Scatterer.jl#L318)

## Internal

---

<a id="method__interpolate.1" class="lexicon_definition"></a>
#### interpolate(s::SDWBA.Scatterer{T},  n) [¶](#method__interpolate.1)
Resample a scatterer's measurement points by interpolating between them. Used
to change the resolution, for instance when increasing the scatterer's body 
size or decreasing the acoustic wavelength.

#### Parameters
- `s` : Scatterer
- `n` : Number of body segments desired in the interpolated scatterer.

#### Returns
A Scatterer with a different number of body segments.


*source:*
[SDWBA/src/Scatterer.jl:116](https://github.com/ElOceanografo/SDWBA.jl/tree/58159dc1cd2fa7416e74887232848ebaba820633/src/Scatterer.jl#L116)

