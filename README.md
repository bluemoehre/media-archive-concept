# media-archive-concept
Concept for storing, archiving and managing large amounts of media regarding folder structures, naming of files, meta tagging based upon Vorbis comment, MKV.


## Audio files


### Metadata


#### Example

| Req   | Field                                           | Multi | Value                                                                 |
| :---: | ----------------------------------------------- | :---: | --------------------------------------------------------------------- |
| ☑     | [TRACK_NUMBER](#track_number)                   | ☐     | 5                                                                     |
| ☑     | [ARTIST](#artist)                               | ☑     | `Axwell` `Ingrosso` `Steve Angello` `Laidback Luke` `Deborah Cox`     |
| ☐     | [ARTIST_DISPLAY](#artist_display)               | ☐     | Axwell, Ingrosso, Steve Angello, Laidback Luke feat. Deborah Cox      |
| ☑     | [TITLE](#title)                                 | ☐     | Leave The World Behind                                                |
| ☐     | [VERSION](#version)                             | ☐     | Dimitri Vegas & Like Mike vs. Shm Dark Forest Edit                    |
| ☑     | [DATE](#date)                                   | ☐     | 2009                                                                  |
| ☑     | [GENRE](#genre)                                 | ☑     | `House`; `Electro`; `Trance`                                          |
| ☑     | [VOCALS](#vocals)                               | ☐     | true                                                                  |
| ☐     | [EXPLICIT](#explicit)                           | ☐     | false                                                                 |
| ☑     | [LANGUAGE](#language)                           | ☑     | `en`                                                                  |
| ☑     | [MOOD](#mood)                                   | ☑     | `happy` `energetic`                                                   |
| ☑     | [TEMPO](#tempo)                                 | ☑     | fast                                                                  |
| ☐     | [BPM](#tempo)                                   | ☑     | 128                                                                   |
| ☑     | [COPYRIGHT](#copyright)                         | ☐     | Axtone Records Ltd. 2009                                              |
| ☑     | [PUBLISHER](#publisher)                         | ☐     | IIP-DDS                                                               |
| ☑     | [RELEASE](#release)                             | ☐     | Leave The World Behind                                                |
| ☑     | [RELEASE_ARTIST](#release_artist)               | ☐     | Axwell, Ingrosso, Steve Angello, Laidback Luke feat. Deborah Cox      |
| ☑     | [RELEASE_DATE](#release_date)                   | ☐     | 2009                                                                  |
| ☑     | [RELEASE_TYPE](#release_type)                   | ☐     | single                                                                |
| ☑     | [RELEASE_TOTAL_TRACKS](#release_total_tracks)   | ☐     | 7                                                                     |
| ☐     | [RELEASE_TOTAL_MEDIUMS](#release_total_mediums) | ☐     | 1                                                                     |
| ☐     | [RELEASE_MEDIUM_NUMBER](#release_medium_number) | ☐     | 1                                                                     |
| ☐     | [RELEASE_MEDIUM_TITLE](#release_medium_title)   | ☐     |                                                                       |
| ☑     | [SOURCE](#source)                               | ☐     | webshop                                                               |
| ☐     | [RETAILER](#retailer)                           | ☐     | Junodownload                                                          |


#### Data Types

- **bool** : `true` or `false`
- **number** : Any numeric value
- **string** : Any unicode text without line-breaks
- **text** : Any unicode text (including line-breaks)
- **date** : Date in the format `YYYY`, `YYYY-MM` or `YYYY-MM-DD`

Note: Due most metadata models are dealing with key/value pairs only, this part is kind of virtual.


#### Special Words

|- Meaning -| Default | Variations |
| --- | --- | --- |
| and | **&** | `,` `+` `x` `and` |
| featuring | **feat.** | `ft.` `featuring` |
| versus | **vs.** | `X` `versus` |

##### Examples

- A, B & C
- X feat. A, B & C
- A vs. B vs. C
- X & Y feat. A vs. B & C


#### Stylized Names

Some artists use non-word characters, special capitalization or special phonetics in their names for design purposes. \
In this case a regular and/or normalized version must be provided, so humans can search in all ways and machines are able to differentiate correctly. \
*Choose wisely how these fields are filled, think on origins and languages and expect some research on the artist! \
Also be prepared for some future changes introduced by labels or bands*

##### Examples

| Stylized | Regular | Normalized |
| --- | --- | --- |
| \*NSYNC<br/>'N Sync `deprecated` | NSYNC | |
| 3OH!3 | 3OH3 | Three Oh Three |
| 3LAU | Blau | |
| DJs @ Work | DJs @ Work | DJs at Work |
| Florence + the Machine | Florence and the Machine | |
| Ich + Ich | Ich und Ich | | 
| JAWNY | Jawny | |
| Ke$ha | Kesha | |
| Raindropz! | Raindropz | Raindrops | 
| Snap! | Snap | |

*Be aware of '+' may be part of the band's name OR to describe a co-production!*


#### Fields

- <a name="track_number">**TRACK_NUMBER**</a> ( `number` ) _optional_; _single-valued_

  The track's number on the release. (When having multiple mediums, this will be serially numbered.)

- <a name="artist">**ARTIST**</a> ( `string` ) _required_; _multi-valued_

  The artists of the track as separated values. \
  These values must only contain artist names. \
  Stylized names must **not** be used but regular ones. \
  By default each artist's name part begins with an upper-case letter.

- <a name="artist_display">**ARTIST_DISPLAY**</a> ( `string` ) _required_; _single-valued_

  The artists of the track as a single string. \
  This string may contain words like `vs.` / `feat.` / `and` / `with`. \
  Stylized names must be used here if available. \
  By default an artist's name begins with an upper-case letter.

- <a name="title">**TITLE**</a> ( `string` ) _required_; _single-valued_

  The track's title

- <a name="version">**VERSION**</a> ( `string` ) _optional_; _single-valued_

  The track's version / edit / remix

- <a name="date">**DATE**</a> ( `date` ) _required_; _single-valued_

  Date when this track was initially published. (Be aware of the difference vs. [**RELEASE_DATE**](#DATE)!)

- <a name="genre">**GENRE**</a> ( `string` ) _required_; _multi-valued_

  All matching genres of the song (in order of ratio descending).

- <a name="vocals">**VOCALS**</a> ( `bool` ) _required_; _single-valued_ 

  `true` if the track contain vocals. \
  `false` if the track is instrumental only.
  
- <a name="explicit">**EXPLICIT**</a> ( `bool` ) _optional_; _single-valued_ 

  `true` if the track contains explicit language. \
  `false` if the track does not contain explicit language.
  
  Defaults to `false` if not set. 
  Must be `false` if present and <a name="vocals">**VOCALS**</a> is `false`.
  
- <a name="language">**LANGUAGE**</a> ( `string` ) _optional_; _multi-valued_ 
  
  Languages used in the track. \
  Values are based upon ISO 639-2.

- <a name="mood">**MOOD**</a> ( `energetic` | `happy` | `bright` | `sad` | `dark` | `agressive` ) _required_; _multi-valued_ 

  Subjective mood of the track in order of quantity descending. \
  @TODO: extend possible values or allow any string

- <a name="tempo">**TEMPO**</a> ( `very slow` | `slow` | `normal` | `fast` | `very fast` | `extreme` ) _required_; _multi-valued_ 

  Subjective tempo of the track in order of quantity descending.

- <a name="bpm">**BPM**</a> ( `number` ) _optional_; _multi-valued_ 

  Average beats per minute **OR** all different values of all sections of the track in order of quantity descending.

- <a name="copyright">**COPYRIGHT**</a> ( `string` ) _optional_; _single-valued_ 

- <a name="publisher">**PUBLISHER**</a> ( `string` ) _required_; _single-valued_ 

- <a name="lyrics">**LYRICS**</a> ( `text` ) _optional_; _single-valued_ 

- <a name="release">**RELEASE**</a> ( `string` ) _required_; _single-valued_

  Title of the release

- <a name="release_artist">**RELEASE_ARTIST**</a> ( `string` ) _required_; _single-valued_

  The official artist of the release. \
  This string may contain text like: `vs.` / `feat.` / `and` / `with`. \
  By default an artist's name begins with an upper-case letter.

- <a name="release_date">**RELEASE_DATE**</a> ( `date` ) _required_; _single-valued_ 

  Date when the release was published. (Be aware of the difference vs. [**DATE**](#DATE)!)

- <a name="release_type">**RELEASE_TYPE**</a> ( `string` ) _required_; _single-valued_ 

  Type of the release (e.g. `single` | `maxi` | `album` | `sampler`)

- <a name="release_total_tracks">**RELEASE_TOTAL_TRACKS**</a> ( `number` ) _optional_; _single-valued_ 

  Total track count of the release. (When having multiple mediums, this will be the total track count of all mediums.)

- <a name="release_total_mediums">**RELEASE_TOTAL_MEDIUMS**</a> ( `number` ) _optional_; _single-valued_ 

  The release's total medium count. (Physical mediums only - e.g. Vinyl / Compact Disc) 

- <a name="release_medium_number">**RELEASE_MEDIUM_NUMBER**</a> ( `number` ) _optional_; _single-valued_ 

  The medium number the track was on. (Physical mediums only - e.g. Vinyl / Compact Disc) 

- <a name="release_medium_title">**RELEASE_MEDIUM_TITLE**</a> ( `string` ) _optional_; _single-valued_ 

  The title of the medium the track was on (e.g. `Side A` | `Summer Disc` | `Mixed by DJ`)

- <a name="source">**SOURCE**</a> ( `string` ) _required_; _single-valued_ 

  Where the file comes from (e.g. `download` | `cd` | `vinyl` )

- <a name="retailer">**RETAILER**</a> ( `string` ) _optional_; _single-valued_ 

  Who sold you the file (e.g. `Junodownload` | `iTunes` | `Beatport`)
