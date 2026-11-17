# 99 Names of Prophet Muhammad ﷺ (Asma-e-Nabi) — JSON Dataset

A clean, ready-to-use JSON dataset of the **99 beautiful names of Prophet Muhammad ﷺ (أسماء النبي)** with vocalized Arabic, transliteration, and meanings in **English and Urdu**.

> "Muhammad is the Messenger of Allah." — *Surah Al-Fath, 48:29*

## Used in the Fajr App

This dataset powers the Names of the Prophet ﷺ section of **[Fajr: Prayer Alarm & Adhan](https://play.google.com/store/apps/details?id=com.alifanalytics.fajr_app)**, an Android app by [Alif Analytics](https://play.google.com/store/apps/details?id=com.alifanalytics.fajr_app).

<a href="https://play.google.com/store/apps/details?id=com.alifanalytics.fajr_app">
  <img alt="Get it on Google Play" src="https://play.google.com/intl/en_us/badges/static/images/badges/en_badge_web_generic.png" height="60">
</a>

**Companion dataset:** [99 Names of Allah (Asma ul Husna) JSON Dataset](https://github.com/anno143/99-Names-of-Allah-Asma-ul-Husna-JSON-Dataset)

## Features

- All 99 names with vocalized Arabic (with harakat)
- Scholarly transliteration (e.g. `Muḥammad`, `Muṣṭafā`, `Khātam al-Anbiyāʾ`)
- English meaning
- **Urdu meaning (اردو)**
- 3 additional names that appear in the Urdu source, kept in a separate `additional` array
- Plain UTF-8 JSON: Arabic and Urdu text is stored as readable characters, not escaped sequences

## File

```
99_Names_Of_Prophet_Muhammad.json
```

## Data Structure

```json
{
  "code": 200,
  "status": "OK",
  "data": [
    {
      "number": 1,
      "name": "مُحَمَّد",
      "transliteration": "Muḥammad",
      "en": {
        "meaning": "Highly Praised"
      },
      "ur": {
        "meaning": "تعریف والا"
      }
    }
  ],
  "additional": [
    {
      "name": "نَبِيُّ الرَّحْمَة",
      "transliteration": "Nabī ar-Raḥmah",
      "en": { "meaning": "The Prophet of Mercy" },
      "ur": { "meaning": "مہربانی والا نبی" }
    }
  ]
}
```

| Field | Type | Description |
|---|---|---|
| `number` | int | Position in the list (1–99) |
| `name` | string | Arabic name, vocalized |
| `transliteration` | string | Latin transliteration |
| `en.meaning` | string | English meaning |
| `ur.meaning` | string | Urdu meaning |
| `additional` | array | Extra names found in the Urdu source but not in the 99 list (no `number`) |

## Usage

Direct link to the raw file:

```
https://raw.githubusercontent.com/anno143/99-Names-of-Prophet-Muhammad-JSON-Dataset/main/99_Names_Of_Prophet_Muhammad.json
```

**JavaScript**

```js
const res = await fetch("https://raw.githubusercontent.com/anno143/99-Names-of-Prophet-Muhammad-JSON-Dataset/main/99_Names_Of_Prophet_Muhammad.json");
const { data } = await res.json();
console.log(data[0].name, data[0].ur.meaning);
```

**Python**

```python
import json

with open("99_Names_Of_Prophet_Muhammad.json", encoding="utf-8") as f:
    names = json.load(f)["data"]

for n in names:
    print(n["number"], n["transliteration"], "-", n["en"]["meaning"], "-", n["ur"]["meaning"])
```

**Dart / Flutter**

```dart
final jsonStr = await rootBundle.loadString('assets/99_Names_Of_Prophet_Muhammad.json');
final List names = json.decode(jsonStr)['data'];
print(names.first['ur']['meaning']);
```

> Tip: Urdu and Arabic are right-to-left. Render them with RTL text direction and a font that supports Arabic script (e.g. Noto Nastaliq Urdu, Noto Naskh Arabic, Amiri). When displaying a name, it is customary to follow it with ﷺ (ṣallallāhu ʿalayhi wa sallam).

## Sources

- **Arabic, numbering and English meanings:** [Usmani Mosque, Leicester: Asma-e-Muhammad (PDF)](https://usmanimosque.com/Name%204.pdf)
- **Urdu meanings:** [Daaiyatul Islam: 99 Names of Prophet Muhammad, Asma-e-Nabi (PDF)](https://daaiyatulislam.wordpress.com/2024/05/25/99-names-of-prophet-muhammad-asma-e-nabi-pdf/)

### Notes on compiling

- The two source lists follow the same order, except that the Urdu list has three extra names: Rasūl ar-Rāḥah, Nabī ar-Raḥmah and Khātam ar-Rusul. The 99 entries follow the Usmani Mosque list, and the three extra names are in `additional`.
- In the Urdu source, the meanings of Sirāj (#84) and Munīr (#85) appear to be swapped. They are corrected here: Sirāj = چراغ (lamp), Munīr = چمکتا ہوا (radiant).
- #50 (Nizārī) has no English meaning in the source; "From the Tribe of Nizar" was added.
- Small spelling fixes were made to the English meanings (e.g. "distributer" → "Distributor", "Externa" → "External").
- Transliterations were standardized to one consistent style.

## A Note on the List

Unlike the 99 Names of Allah, there is no single authoritative hadith that lists 99 names of the Prophet ﷺ. Some names (Muhammad, Ahmad, al-Mahi, al-Hashir, al-Aqib) are reported in Sahih al-Bukhari and Sahih Muslim, while many others are titles and descriptions taken from the Quran and Sunnah. Different traditions list different names, and several, such as Ṭā-Hā and Yā-Sīn, are the opening letters of surahs (*huruf muqatta'at*) whose meaning is known to Allah. Meanings here are short translations to aid understanding, not a substitute for scholarly explanation.

## Contributing

Corrections are welcome, especially for translations. Please open an issue or a pull request with the name number, the field, and a source for the correction.

## Credits

- English list: [Usmani Mosque, Leicester](https://usmanimosque.com/Name%204.pdf)
- Urdu list: [Daaiyatul Islam](https://daaiyatulislam.wordpress.com/2024/05/25/99-names-of-prophet-muhammad-asma-e-nabi-pdf/)
- Compilation: [Alif Analytics](https://play.google.com/store/apps/details?id=com.alifanalytics.fajr_app)

## License

Free to use in personal and commercial projects. Please keep a link back to this repository and to the original sources.
