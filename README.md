# Classification-of-Astronomical-light-Curve
The time-series data in this repo are of individual sources detected in the night-sky by telescopes located in Hawaii. These specific sources were selected due to their time-varying nature, i.e. their brightness changes substantially over a period of time. The particularities of these "light curves" may provide valuable information to the nature of the astronomical event that caused them, and the statistical properties of the group as a whole may also give further insights.

View the [introduction slide-deck here](https://github.com/thespacedoctor/astro-analytathon/blob/master/slide-deck.pdf). 


The unique identifier (`uuid`) is all you need to be concerned with, and it is with this `uuid` you can find the distance to the object in the `object_distances.txt` file (more below).

Within the `/data` folder of this repo, are the 645 space-separated, plain-text files containing the time-series data; one file per object. Each row in the file represents a set of properties of the object as measured from a single telescope image.

Files have the following columns:

```text
MJD
m
dm
uJy
duJy
F
err
chi/N
RA
Dec
x
y
maj
min
phi
apfit
mag5sig
Sky
Obs
```
## Data Format

There are 645 objects in this set and their data are recorded in individual plain-text files in the `/data` folder of the repo.

Each file is named as so:

```plain
<uuid>_xxxx_diff.txt
```

for example:

```plain
1090332400212000800_2762_diff.txt
```

Not all columns are useful for time-series analysis; but here are the definitions for those that definitely are:

| Column  | Definition |
| :------------ | :----------- |
| `MJD`     | [Modified Julian Date](https://scienceworld.wolfram.com/astronomy/ModifiedJulianDate.html). A datetime-format preferred by astronomers, with units of days. |
| `uJy`     |  The object's flux (brightness) as measured from a single telescope image.  |
| `duJy`     | The error associated with the measured flux above.  |
| `F`     | Colour-filter used during the telescope observation. `o` orange, `c` cyan. |
| `chi/N` | A *possible* indication of the quality of the flux measurement (unrelated to `duJy`, lower is better) |

### Distance Catalogue

In the root of the repo you will also find a file call `object_distances.csv`. This is a catalogue containing a measurement of the distance to each source. The 2 columns are the `uuid`of the object and `distance_mpc`, the distance to the source in units of megaparsecs (Mpc). 1 Mpc ≈ 3.09E+22 m.

## Suggestions for data-processing:

- for much of these time-series data the object will display no activity, with flux hovering around zero. It's best to focus on the period(s) of time where the object brightens above this base-line, near-zero flux level.
- you may want to differentiate data taken in each of the 2 filters. 

![image](https://user-images.githubusercontent.com/90794121/216454098-f8fca386-34c1-4e26-89a7-91153c59bb6c.png)
![image](https://user-images.githubusercontent.com/90794121/216454204-55fb3609-f199-4458-8bc7-bc927f8e789a.png)
![image](https://user-images.githubusercontent.com/90794121/216454302-76bc829f-fb72-424d-9640-34a8738aeae2.png)


