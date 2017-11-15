# media-archive-concept
Concept for storing, archiving and managing large amounts of media regarding folder structures, naming of files, meta tagging based upon Vorbis comment, MKV.


## Audio files


### Metadata


#### Example

| Req   | Field                                           | Multi | Value                                                                 |
| :---: | ----------------------------------------------- | :---: | --------------------------------------------------------------------- |
| ☑     | [TRACK_NUMBER](#TRACK_NUMBER)                   | ☐     | 5                                                                     |
| ☑     | [ARTIST](#ARTIST)                               | ☐     | `Axwell`; `Ingrosso`; `Steve Angello`; `Laidback Luke`; `Deborah Cox` |
| ☐     | [ARTIST_DISPLAY](#ARTIST_DISPLAY)               | ☑     | Axwell, Ingrosso, Steve Angello, Laidback Luke feat. Deborah Cox      |
| ☑     | [TITLE](#TITLE)                                 | ☐     | Leave The World Behind                                                |
| ☐     | [VERSION](#VERSION)                             | ☐     | Dimitri Vegas & Like Mike vs. Shm Dark Forest Edit                    |
| ☑     | [DATE](#DATE)                                   | ☐     | 2009                                                                  |
| ☑     | [GENRE](#GENRE)                                 | ☑     | `House`; `Electro`; `Trance`                                          |
| ☑     | [VOCALS](#VOCALS)                               | ☐     | true                                                                  |
| ☑     | [MOOD](#MOOD)                                   | ☑     | true                                                                  |
| ☑     | [TEMPO](#TEMPO)                                 | ☑     | fast                                                                  |
| ☐     | [BPM](#TEMPO)                                   | ☑     | 128                                                                   |
| ☑     | [COPYRIGHT](#COPYRIGHT)                         | ☐     | Axtone Records Ltd. 2009                                              |
| ☑     | [PUBLISHER](#PUBLISHER)                         | ☐     | IIP-DDS                                                               |
| ☑     | [RELEASE](#RELEASE)                             | ☐     | Leave The World Behind                                                |
| ☑     | [RELEASE_ARTIST](#RELEASE_ARTIST)               | ☐     | Axwell, Ingrosso, Steve Angello, Laidback Luke feat. Deborah Cox      |
| ☑     | [RELEASE_DATE](#RELEASE_DATE)                   | ☐     | 2009                                                                  |
| ☑     | [RELEASE_TYPE](#RELEASE_TYPE)                   | ☐     | single                                                                |
| ☑     | [RELEASE_TOTAL_TRACKS](#RELEASE_TOTAL_TRACKS)   | ☐     | 7                                                                     |
| ☐     | [RELEASE_TOTAL_MEDIUMS](#RELEASE_TOTAL_MEDIUMS) | ☐     | 1                                                                     |
| ☐     | [RELEASE_MEDIUM_NUMBER](#RELEASE_MEDIUM_NUMBER) | ☐     | 1                                                                     |
| ☐     | [RELEASE_MEDIUM_TITLE](#RELEASE_MEDIUM_TITLE)   | ☐     |                                                                       |
| ☑     | [SOURCE](#SOURCE)                               | ☐     | webshop                                                               |
| ☐     | [RETAILER](#RETAILER)                           | ☐     | Junodownload                                                          |


#### Data Types

- **bool** : `true` or `false`
- **number** : Any numeric value
- **string** : Any unicode text without line-breaks
- **text** : Any unicode text (including line-breaks)
- **date** : Date in the format `YYYY`, `YYYY-MM` or `YYYY-MM-DD`

Note: Due most metadata models are dealing with key/value pairs only, this part is kind of virtual.


#### Fields

- **TRACK_NUMBER** ( `number` ) _optional_; _single-valued_ \
  The track's number on the release. (When having multiple mediums, this will be serially numbered.)

- **ARTIST** ( `string` ) _required_; _multi-valued_ \
  The artists of the track as separated values. \
  These values must only contain artist names. \
  By default each artist's name part begins with an upper-case letter.

- **ARTIST_DISPLAY** ( `string` ) _required_; _single-valued_ \
  The artists of the track as a single string. \
  This string may contain text like: `vs.` / `feat.` / `and` / `with`. \
  By default an artist's name begins with an upper-case letter.

- **TITLE** ( `string` ) _required_; _single-valued_ \
  The track's title

- **VERSION** ( `string` ) _optional_; _single-valued_ \
  The track's version / edit / remix

- **DATE** ( `date` ) _required_; _single-valued_ \
  Date when this track was initially published. (Be aware of the difference vs. [**RELEASE_DATE**](#DATE)!)

- **GENRE** ( `string` ) _required_; _multi-valued_ \
  All matching genres of the song (in order of ratio descending).

- **VOCALS** ( `bool` ) _required_; _single-valued_ \
  `True` if the track contain vocals. \
  `False` if the track is instrumental only.

- **MOOD** ( `happy` | `bright` | `sad` | `dark` ) _required_; _single-valued_ \
  Subjective mood of the track. \
  @TODO: extend possible values or allow any string

- **TEMPO** ( `very slow` | `slow` | `normal` | `fast` | `very fast` | `extreme` ) _required_; _multi-valued_ \
  Subjective tempo of the track.

- **BPM** ( `number` ) _optional_; _multi-valued_ \
  Average beats per minute **OR** all different values of all sections of the track in order of quantity descending.

- **COPYRIGHT** ( `string` ) _optional_; _single-valued_ 

- **PUBLISHER** ( `string` ) _required_; _single-valued_ 

- **LYRICS** ( `text` ) _optional_; _single-valued_ 

- **RELEASE** ( `string` ) _required_; _single-valued_ \
  Title of the release

- **RELEASE_ARTIST** ( `string` ) _required_; _single-valued_ \
  The official artist of the release. \
  This string may contain text like: `vs.` / `feat.` / `and` / `with`. \
  By default an artist's name begins with an upper-case letter.

- **RELEASE_DATE** ( `date` ) _required_; _single-valued_ \
  Date when the release was published. (Be aware of the difference vs. [**DATE**](#DATE)!)

- **RELEASE_TYPE** ( `string` ) _required_; _single-valued_ \
  Type of the release (e.g. `single` | `maxi` | `album` | `sampler`)

- **RELEASE_TOTAL_TRACKS** ( `number` ) _optional_; _single-valued_ \
  Total track count of the release. (When having multiple mediums, this will be the total track count of all mediums.)

- **RELEASE_TOTAL_MEDIUMS** ( `number` ) _optional_; _single-valued_ \
  The release's total medium count. (Physical mediums only - e.g. Vinyl / Compact Disc) 

- **RELEASE_MEDIUM_NUMBER** ( `number` ) _optional_; _single-valued_ \
  The medium number the track was on. (Physical mediums only - e.g. Vinyl / Compact Disc) 

- **RELEASE_MEDIUM_TITLE** ( `string` ) _optional_; _single-valued_ \
  The title of the medium the track was on (e.g. `Side A` | `Summer Disc` | `Mixed by DJ`)

- **SOURCE** ( `string` ) _required_; _single-valued_ 
  Where the file comes from (e.g. `download` | `cd` | `vinyl` )

- **RETAILER** ( `string` ) _optional_; _single-valued_ 
  Who sold you the file (e.g. `Junodownload` | `iTunes` | `Beatport`)
