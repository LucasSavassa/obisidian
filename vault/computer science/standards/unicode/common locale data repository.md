https://www.unicode.org/reports/tr35/#Introduction

![[Pasted image 20250605171442.png]]
[[iana]] defines subtags in [[language subtag registry]], following [[bcp 47]]
CLDR uses the tags to provides **rich locale data** to them

# example
```xml
<ldml>
  <identity>
    <language type="fr"/>
    <territory type="FR"/>
  </identity>

  <dates>
    <calendars>
      <calendar type="gregorian">
        <dateFormats>
          <dateFormatLength type="medium">
            <dateFormat>
              <pattern>dd/MM/y</pattern>
            </dateFormat>
          </dateFormatLength>
        </dateFormats>
      </calendar>
    </calendars>
  </dates>

  <numbers>
    <symbols numberSystem="latn">
      <decimal>,</decimal>
      <group> </group>
    </symbols>
    <currencies>
      <currency type="EUR">
        <symbol>€</symbol>
        <displayName>euro</displayName>
      </currency>
    </currencies>
  </numbers>

  <localeDisplayNames>
    <languages>
      <language type="en">anglais</language>
      <language type="de">allemand</language>
    </languages>
    <territories>
      <territory type="US">États-Unis</territory>
      <territory type="CA">Canada</territory>
    </territories>
  </localeDisplayNames>
</ldml>
```

