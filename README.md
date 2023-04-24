# 1. Importformate / Inbound Messages (XML)

Unser System bietet die Möglichkeit aus verschiedenen Formaten Informationen zu beziehen.\
Die nachfolgenden Formate definieren unsere XML- und CSV-Schnittstellen.

Natürlich besteht die Möglichkeit, dass individuelle Formate auf Kundenwunsch implementiert werden.\
Der Aufwand für die individuelle Entwicklung für Ihr System/Format\
kann mit dem Vertrieb der QTRADO Logistics besprochen werden.

## 1.1. PRICAT - Artikelstammdaten / Product Master Data (XML)

Bitte Artikelstammdaten als CSV oder Excel senden.

## 1.2. ORDERS - Aufträge / Sales Orders (Outbound Goods)

Mit diesem Format können sie uns einen Warenausgang (Lieferung an Dritte oder sie selbst) melden.

Es gibt keine Vorgabe für den Dateinamen außer dass er auf ".xml" enden muss.\
Wir empfehlen jedoch einen sprechenden Namen zu vergeben.

Nachfolgend nun die Schemabeschreibung.

**Bitte beachten sie unbedingt auch die weiteren Informationen (mehr...) bei den diversen Feldern.**

<details>
<summary>Schemabeschreibung des ORDERS-Formats</summary>

Schema: ORDERS.XSD


 |   Pos.    |   Name                        |  Description                 |  Data Type (length)  |  Mandatory  |
 |----------:|-------------------------------|------------------------------|----------------------|:-----------:|
 | 1         |**Header**|||X|
 | 2         |EdiPartnerCode                 |Erhalten Sie durch unsere IT  |string constant       | X           |
 | 3         |TenantId                       |Debitor-Nr., erhalten Sie durch unseren Vertrieb|string constant| X|
 | 4         |Date                           |Datum/Zeit-Stempel            |datetime              | X           |
 | 5         |FileType                       |Orders                        |string constant       | X           |
 | 6         |Remotesystem                   |Erhalten Sie durch unsere IT  |string constant       | X           |
 | 7         |**Orders / Order**|||X|
 | 8         |Document_Type                  |*Reserviert*                  |string                |             |
 | 9         |CustomerOrderNo                |Ihre Auftrags-Nr.             |string (35)           | X           |
 |10         |PaymentMethodCode              |Zahlungsart                   |string                |             |
 |11         |OrderTotal                     |Auftragswert inkl. MwSt.      |decimal               |             |
 |12         |ShippingAdvise                 |Teil-/Komplettlieferung       |string enum Complete,Partial|       |
 |13         |ExpressOrder                   |Auftrag mit hoher Priorität [mehr...](#termin--und-expressversand) |string enum           |             |
 |14         |ReferenceText                  |Referenztext, z. B. Bestellnummer ihres Kunden|string (35)|        |
 |15         |LanguageCode                   |Sprachcode des Dokumentes     |string( 10)           |             |
 |16         |CustomerSalesPersonName        |Name des Sachbearbeiters      |string (50)           |             |
 |17         |CustomerSalesPersonPhone       |Telefonnr. Sachbearbeiter     |string (60)           |             |
 |18         |CustomerSalesPersonFax         |Faxnr. Sachbearbeiter         |string (60)           |             |
 |19         |CustomerSalesPersonEmail       |E-Mail Sachbearbeiter         |string (80)           |             |
 |20         |CustomerSalesOrganizationalUnit|Abteilung, Niederlassung etc. |string (50)           |             |
 |21         |OrderedByName                  |Name des Bestellers           |string (30)           |             |
 |22         |OrderedByEmail                 |Email des Bestellers          |string (80)           |             |
 |23         |BillToName                     |Rechnung-An Name, Zeile 1     |string (50)           |             |
 |24         |BillToName2                    |Rechnung-An Name, Zeile 2     |string (50)           |             |
 |25         |BillToContact                  |Rechnung-An Kontakt           |string (50)           |             |
 |26         |BillToAddress                  |Rechnung-An Adresse (Straße + Haus-Nr.)          |string (50)           |             |
 |27         |BillToPostCode                 |Rechnung-An PLZ               |string (20)           |             |
 |28         |BillToCity                     |Rechnung-An Ort               |string (30)           |             |
 |29         |BillToCounty                   |Bei Ländern in denen zutreffend, Bezirk/Landkreis         |string (30)           |             |
 |30         |BillToCountryRegionCode        |Länderkürzel (ISO 3166-2) [mehr...](#identifikation-von-ländern)  |string (2)            |             |
 |31         |ShipToName                     |Liefer-An Name, Zeile 1 [mehr...](#vorgaben-für-lieferanschrift)   |string (50)           | X           |
 |32         |ShipToName2                    |Liefer-An Name, Zeile 2 [mehr...](#vorgaben-für-lieferanschrift)   |string (50)           |             |
 |33         |ShipToContact                  |Liefer-An Kontakt [mehr...](#vorgaben-für-lieferanschrift)         |string (50)           |             |
 |34         |ShipToAddress                  |Liefer-An Adresse (Straße + Haus-Nr.) [mehr...](#vorgaben-für-lieferanschrift)             |string (50)           | X           |
 |35         |ShipToPostnummer               |Packstation-Nr. [mehr...](#lieferung-an-packstation)           |string (30)           |             |
 |36         |ShipToPostCode                 |Liefer-An PLZ [^7]             |string (20)           | X           |
 |37         |ShipToCity                     |Liefer-An Ort [mehr...](#vorgaben-für-lieferanschrift)              |string (30)           | X           |
 |38         |ShipToCounty                   |Bei Ländern in denen zutreffend, Bezirk/Landkreis         |string (30)           |             |
 |39         |ShipToCountryRegionCode        |Länderkürzel (ISO 3166-2) [mehr...](#identifikation-von-ländern)  |string (2)            | X           |
 |40         |ShipToEmail                    |Email-Adresse des Warenempfängers            |string (80)           |             |
 |41         |ShipToPhoneNo                  |Telefonnummer des Warenempfängers            |string (30)           |             |
 |42         |ShipToTourSequence             |Fahrfolge, interne Verwendung |string (20)           |             |
 |43         |ShipComment                    |Versandsbemerkung             |string                |             |
 |44         |ShippingAgentCode              |Versanddienstleister          |string                |             |
 |45         |ShippingAgentServiceCode       |Versandtyp                    |string                |             |
 |46         |ShipmentDate                   |Warenausgangsdatum [mehr...](#termin--und-expressversand)        |date, DD.MM.YYYY      |             |
 |47         |**Order / Instructions / Instruction**||||
 |48         |InstructionName                |Handlungsanweisung, Name      |string                | X           |
 |49         |**Order / Attachments / Attachment**||||
 |50         |Description                    | Bezeichnung der Datei        |string (30)           | X           |
 |51         |Filename                       | Dateiname [mehr...](#dateianhänge)                |string (255)          | X           |
 |52         |**Order / Products / Product**|||X|
 |53         |Type                           |Typ von Produkt               |string enum           |             |
 |54         |CustomerLineNo                 |Auftragsposition              |string (20)           |             |
 |55         |Quantity                       |Menge                         |integer               | X           |
 |56         |DepositCustomerItemNo          |Artikel-Nr. / SKU             |string (30)           | X           |
 |57         |Description1                   |Beschreibung 1                |string (50)           |             |
 |58         |Description2                   |Beschreibung 2                |string (50)           |             |
 |59         |UnitPrice                      |Einzelpreis                   |decimal               |             |
 |60         |QtyPerUnitOfMeasure            |Menge pro Einheit             |integer               |             |
 |61         |UnitOfMeasureCode              |Einheit                       |String (10)           |             |
 |62         |UnitWeight                     |Einzelgewicht                 |decimal               |             |
 |63         |LotNo                          |Chargenummer                  |string (20)           |             |
 |64         |SerialNo                       |Seriennummer                  |string (20)           |             |

</details>

### 1.2.1 Weitere Hinweise zu einzelnen Feldern des ORDERS-Formats

#### Identifikation von Ländern
Länder werden immer anhand ihres eindeutigen zweistelligen ISO 3166-2 Codes (z.B. DE, AT, CH) identifiziert,\
um abweichende oder postalisch falsche Schreibweisen zu vermeiden.

#### Postleitzahlvalidierung
Postleitzahlen werden in Vernindung mit dem Lieferland gegen Prüfmuster der EZB validiert.\
Die Prüfmuster finden Sie in der Datei\
List_postal_code_formatting_rules_and_regular_expressions_with_Annotations.xlsx

#### Vorgaben für Lieferanschrift

Einige Versender, wie z. B. DHL unterstützen bei Straßennamen nur 30 Zeichen.\
Sofern möglich, empfehlen wir dies für ihre Systeme zu berücksichtigen.

Bedingt durch die Vorgaben der Versanddienstleister und unser WMS muss eine Lieferanschrift\
eindeutig durch die Felder ShipToName, ShipToName2, ShipToAddress, ShipToPostCode, ShipToCity, ShipToCountryRegionCode definiert sein.

Sie können diese Felder, wie nachstehend beschrieben, nutzen.

ShipToName: Firmenname oder Name des Empfängers, wenn es keinen Firmennamen gibt, da dieses Feld gefüllt sein muss.

ShipToName2: Firmenzusatz oder Name des Empfängers, wenn es einen Firmennamen gibt.

ShipToContact: Name des Empfängers, wenn ShipToName und ShipToName2 gefüllt sind.

Beispiele:

    ShipToName: Muster Handels GmbH
    ShipToName2: Peter Meier
    ShipToContact:

    ShipToName: Musterhandels GmbH
    ShipToName2: c/o Andere Firma
    ShipToContact: Peter Meier

    ShipToName: Peter Meier
    ShipToName2:
    ShipToContact:

    ShipToName: Musterhandles GmbH
    ShipToName2:
    ShipToContact: Peter Meier

Ist ShipToCountryRegionCode nicht gefüllt, wird Deutschland als Lieferland angenommen.

Das Feld ShipToContact kann optional genutzt werden.

```
Das Feld ShipToContact wird leider nicht von allen Versanddienstleistern unterstützt. Z. B. DPD
```

```
Wir weisen darauf hin, dass sie für die Übermittlung einer korrekten Empfängeradresse verantwortlich sind!
```

#### Lieferung an Packstation
Soll die Lieferung an eine Packstation oder eine Postfiliale gehen,\
ist die jeweilige Packstation oder Postfiliale im Feld „ShipToAddress" zu speichern.\
Die Postnummer wird in das Feld „ShipToPostnummer" ausgegeben.\
Handelt es sich nicht um eine Lieferung an eine Packstation oder Postfiliale,\
ist das Feld „ShipToPostnummer" leer zu lassen.

Alternativ können sie die Anschrift gemäß den Vorgaben von DHL über die\
Felder ShipToName und ShipToName2 und ShipToAddress selbst formatieren.

Beispiel:

  Max Mustermann
  898989898
  Packstation 33
  99999 Musterstadt

#### Dateianhänge
Dateiname des Dokumentes z. B. original Lieferschein.pdf.\
Anhand des Namens wird die Datei vom vorgegebenen Ordner runtergeladen und dem Auftrag zugewiesen.\
**Dies ist ein Pflichtfeld**, wenn ein Anhang übermittelt werden soll.\
**Es ist zwingend erforderlich, dass die Dateien vor den Aufträgen hochgeladen werden.**

#### Termin- und Expressversand
Bitte stimmen sie die Verwendung dieser Funktion mit dem Vertrieb ab.\
Die terminierte Auslieferung eines Auftrages (gewünschtes Warenausgangsdatum),\
benötigt besondere Vorkehrungen und kann Auswirkungen auf die Auslieferung haben.

### 1.2.2. Weitere Hinweise zum Format und zur Verarbeitung von Aufträgen

Bei der Erstellung der XML-Datei können sie Felder, die kein Pflichtfeld sind,\
entweder leer lassen oder das XML-Tag gar nicht ausgeben.\
Dies wird in der Verarbeitung nicht zu einem Fehler führen.

Validieren sie ihre XML-Datei bitte gegen die Schemadatei ORDERS.xsd.

**Es ist nicht möglich einen Auftrag doppelt an unser System zu melden**.\
Finden wir bei uns im System unter ihrer Kundennummer einen Auftrag oder\
eine Lieferung mit derselben CustomerOrderNo, wird der erneute Import abgelehnt.

Dies hat auch zur Folge,\
dass **Auftragsänderungen nicht automatisiert an uns übermittelt werden können**.\
Setzen Sie sich dazu bitte mit ihrem Ansprechpartner in der Kundenbetreuung in Verbindung.

Aufträge werden von uns periodisch, im Standard alle 5 Minuten, abgeholt.\
Dabei berücksichtigen wir bei Dateien das letzte Änderungsdatum.

Sollte es während eines Laufes Aufträge geben, die in mehreren Dateien enthalten sind,\
wird nur die neueste Version des Auftrages berücksichtigt.\
Wir identifizieren einen Auftrag dabei anhand der CustomerOrderNo.

## 1.3. PURCHASEORDER - Einkaufsbestellung (Wareneingangsankündigung) / Purchaseorder (Inbound Goods) (XML)

Mit diesem Format können sie uns einen geplanten Wareneingang melden.

Es gibt keine Vorgabe für den Dateinamen außer dass er auf ".xml" enden muss.\
Wir empfehlen jedoch einen sprechenden Namen zu vergeben.

Nachfolgend nun die Schemabeschreibung.

<details>
<summary>Schemabeschreibung des PURCHASEORDERS-Formats</summary

Schema: PurchaseOrders.xsd

  |   Pos.    |   Name                        |  Description                 |  Data Type (length)  |  Mandatory  |
  |----------:|-------------------------------|------------------------------|----------------------|:-----------:|
  | 1         |**Header**|||X|
  | 2         |EdiPartnerCode                 |Erhalten Sie durch unsere IT  |string constant       | X           |
  | 3         |TenantId                       |Debitor-Nr., erhalten Sie durch unseren Vertrieb|string constant| X|
  | 4         |Date                           |Datum/Zeit-Stempel            |datetime              | X           |
  | 5         |FileType                       |Orders                        |string constant       | X           |
  | 6         |Remotesystem                   |Erhalten Sie durch unsere IT  |string constant       | X           |
  | 7         |**PurchaseOrders / PurchaseOrder**|||X|
  | 8         |Document_Type                  |*Reserviert*                  |string                |             |
  | 9         |CustomerOrderNo                |Ihre Bestell-Nr.              |string (35)           | X           |
  |10         |ExpectedReceiptDate            |Wareneingangsdatum            |date, DD.MM.YYYY      |             |
  |11         |ReferenceText                  |Referenztext/-nummer          |string (35)           |             |
  |12         |VendorShipmentNo               |Lieferscheinrn. Lieferant     |string (35)           |             |
  |13         |ShippedFromName                |Lieferant Name, Zeile 1       |string (50)           |             |
  |14         |ShippedFromName2               |Lieferant Name, Zeile 2       |string (50)           |             |
  |15         |ShippedFromContact             |Lieferant Kontakt             |string (50)           |             |
  |16         |ShippedFromAddress             |Lieferant, Straße + Hausnr.   |string (50)           |             |
  |17         |ShippedFromPostCode            |Lieferant, Postleitzahl       |string (20)           |             |
  |18         |ShippedFromCity                |Lieferant, Ort                |string (30)           |             |
  |19         |ShippedFromCounty              |Lieferant, Bezirk/Landkreis   |string (30)           |             |
  |20         |ShippedFromCountryRegionCode   |Lieferant, Länderkürzel ISO2  |string (2)            |             |
  |21         |ShippedFromEmail               |Lieferant, Email              |string (80)           |             |
  |22         |Comment                        |Kommentar                     |string                |             |
  |23         |**PurchaseOrder / Attachments / Attachments**||||
  |24         |Description                    |Beschreibung der Datei        |string (30)           | X           |
  |25         |Path                           |Dateiname                     |string (255)          | X           |
  |26         |**PurchaseOrder / Products / Product**|||X|
  |27         |CustomerLineNo                 |Zeilenreferenz Bestellposition|string (20)           |             |
  |28         |DepositCustomerItemNo          |Artikelnr. / SKU              |string (30)           | X           |
  |29         |Description1                   |Artikelbeschreibung, Zeile 1  |string (50)           |             |
  |30         |Description2                   |Artikelbeschreibung, Zeile 2  |string (50)           |             |
  |31         |Quantity                       |Menge                         |integer               | X           |
  |32         |UnitOfMeasureCode              |Einheit, ggf. Mapping erford. |string (20)           |             |
  |33         |QtyPerUnitOfMeasure            |Menge (Basis) pro Einheit     |integer               |             |
  |34         |LotNo                          |Chargennummer                 |string (20)           |             |
  |35         |SerialNo                       |Seriennummer                  |string (20)           |             |
  |36         |ExpirationDate                 |Ablaufdatum/MHD               |date, DD.MM.YYYY      |             |
 
 </details>

# 2. Rückmeldungen / Outbound Messages (XML)

## 2.1. DESADV - Lieferschein / Delivery Note (XML)

In der DESADV Datei erhalten sie Informationen zu einem ausgelieferten Auftrag.

Dateiname: DESADV_*.xml

<details>
<summary>Schemdefinition des DESADV-Formats>

Schema: Desadv.xsd

 |   Pos.    |   Name                        |  Description                 |  Data Type (length)  |
 |----------:|-------------------------------|------------------------------|----------------------|
 | 1         |**Shipment**||||
 | 2         |DocumentType                   | Festwert: 351                |                      |
 | 3         |TransferFlag                   | 0 Erstsendung, 1 Wiederholung|                      |
 | 5         |CustomerNo                     | Interne Kundennummer         |string (20)           |
 | 6         |ShipmentNo                     | Lieferscheinnummer           |string (20)           |
 | 7         |ShipmentDate                   | Lieferdatum                  |date, DD.MM.YYYY      |
 | 8         |**Shipment / Customer_Address**||||
 | 9         |No                             | Interne Kundennr im Mandanten|string (20)           |
 |10         |CustomerGLN                    | Globale Loationsnummer       |string (13)           |
 |11         |Name                           | Kundenname, Zeile 1          |string (50)           |
 |12         |Name2                          | Kundenname, Zeile 2          |string (50)           |
 |13         |Address                        | Straße + Hausnummer          |string (50)           |
 |14         |Address2                       | Adresszusatz                 |string (50)           |
 |15         |PostCode                       | Postleitzahl                 |string (20)           |
 |16         |City                           | Ort                          |string (30)           |
 |17         |CountryRegionCode              | Länderkürzel, ISO-ALPHA2     |string (2)            |
 |18         |**Shipment / Billing_Address**||||
 |19         |BillToCustomerNo               | Interne Kundennr im Mandanten|string (20)           |
 |20         |BillToCustomerGLN              | Globale Loationsnummer       |string (13)           |
 |21         |BillToName                     | Kundenname, Zeile 1          |string (50)           |
 |22         |BillToName2                    | Kundenname, Zeile 2          |string (50)           |
 |23         |BillToAddress                  | Straße + Hausnummer          |string (50)           |
 |24         |BillTAddress2                  | Adresszusatz                 |string (50)           |
 |25         |BillToPostCode                 | Postleitzahl                 |string (20)           |
 |26         |BillToCity                     | Ort                          |string (30)           |
 |27         |BillToCountryRegionCode        | Länderkürzel, ISO-ALPHA2     |string (2)            |
 |28         |**Shipment / Shipping_Address**||||
 |29         |ShipToCustomerNo               | Interne Kundennr im Mandanten|string (20)           |
 |31         |ShipToName                     | Kundenname, Zeile 1          |string (50)           |
 |32         |ShipToName2                    | Kundenname, Zeile 2          |string (50)           |
 |33         |ShipToAddress                  | Straße + Hausnummer          |string (50)           |
 |34         |ShipTAddress2                  | Adresszusatz                 |string (50)           |
 |35         |ShipToPostCode                 | Postleitzahl                 |string (20)           |
 |36         |ShipToCity                     | Ort                          |string (30)           |
 |37         |ShipToCountryRegionCode        | Länderkürzel, ISO-ALPHA2     |string (2)            |
 |38         |**Shipment / ShipmentLines**||||
 |39         |PosNo                          | Positionsnummer              |integer               |
 |40         |ItemNo                         | Interne Artikel ID           |integer               |
 |41         |GTIN                           | Global Trade Item Number     |string (13)           |
 |42         |GTINBaseUnitOfMeasure          | GTIN Basiseinheit            |string (13)           |
 |43         |CustomerItemNo                 | Kundenartikelnummer/SKU      |string (30)           |
 |44         |ItemDescription1               | Artikelbezeichnung, Zeile 1  |string (50)           |
 |45         |ItemDescription2               | Artikelbezeichnung, Zeile 2  |string (50)           |
 |46         |Quantity                       | Menge                        |integer               |
 |47         |UnitOfMeasureCode              | Einheit                      |string (10)           |
 |48         |TotalPieces                    | Gesamtstückzahl, geliefert   |integer               |
 |49         |QuantityBase                   | Menge, Basiseinheit          |integer               |
 |50         |CustomerOrderNo                | Kunden Auftragsreferenz      |string (35)           |
 |51         |CustomerOrderLineNo            | Kunden Auftragszeilenref.    |string (20)           |
 |52         |**Shipment / ShipmentLines / ItemTracking / ItemTrackingLine**||||
 |53         |TrackItemNo                    | QL interne Artikelnummer     |integer               |
 |54         |TrackCustomerItemNo            | Kunden Artikelnr.            |string (30)           |
 |55         |TrackItemDescription           | Artikelbezeichnung           |string (50)           |
 |56         |TrackShipmentLineNo            | Lieferscheinzeilennr.        |integer               |
 |57         |TrackQuantity                  | Menge für Charge/Seriennr.   |integer               |
 |58         |TrackLotNo                     | Chargennummer                |string (20)           |
 |59         |TrackSerialNo                  | Seriennummer                 |string (20)           |
 |60         |TrackExpirationDate            | Ablaufdatum/MHD              |date, DD.MM.YY        |
 |62         |ParcelNo                       | Sendungsnummer               |string (20)           |
 |63         |Weight                         | Gewicht                      |decimal               |
 |64         |ShippingAgent                  | Versand-Dienstleister        |string                |
 |65         |ServiceDescription             | Versandoption                |string                |
 |66         |TrackingURL                    | Tracking URL                 |string                |

 </details>

## 2.2. INVRPT - Bestandsmeldung / Inventory Report (XML)

Durch die INVRPT Datei erhalten Sie die Bestandsinformation zu Artikeln

Dateiname: INVRPT_*.xml

<details>
<summary>Schemadefinition des INVRPT-Formats</summary>

 |   Pos.    |   Name                        |  Description                 |  Data Type (length)  |
 |----------:|-------------------------------|------------------------------|----------------------|
 | 1         |**Message**||||
 |2|Type|Festwert: INVRPT|||
 |3|VendorGLN|Globale Lokationsnummer Lieferant|string (13)|
 |4|CustomerGLN|Globale Lokationsnummer Kunde|string (13)|
 |5|CustomerNo|Debitor-Nr., intern|string|
 |6|DateTime|Datum/Zeit-Stempel|datetime yyyyMMddHHmmss|
 |7|**Items / Item**||||
 |8|ItemNo|Interne Artikel-Nr.|integer|
 |9|CustomerItemNo|Kunden Artikel-Nr.|string|
 |10|Description|Artikelbezeichnung|string|
 |11|QtyTotal|Gesamtbestand|integer|
 |12|QtyAvailableForSale|Menge verfügbar für Verkauf|integer|
 |13|QtyBlocked|Menge gesperrt|integer|
 |14|QtyReserved|Menge reserviert|integer|
 |15|QtyInDepositOrder|Menge in Einlagerauftrag (Wareneingang)|integer|
 |16|QtyInDislocationOrder|Menge in Auslagerauftag (Warenausgang)|integer|

</details>

## 2.3. ITMLEDG - Artikelposten / Item Ledger Entries (XML)

Mit diesem Format übermitteln wir ihnen Artikelposten (Bestandsveränderungen).\
Diese werden in Verbindung mit z.B. Wareneingängen, Retouren, manuellen Korrekturen oder Inventuren erzeugt.

Dateiname: ITMLEDG_*.xml

<details>
<summary>Schemadefinition des ITMLEDG-Formats</summary>

|   Pos.    |   Name                        |  Description                 |  Data Type (length)  |
|----------:|-------------------------------|------------------------------|----------------------|
|1|**Message**||||
|2|Type|Festwert: ITMLEDG||
|3|VendorGLN|Globale Lokationsnummer Lieferant|string (13)|
|4|CustomerGLN|Globale Lokationsnummer Kunde|string (13)|
|5|CustomerNo |Debitor-Nr., intern|string (20)|
|6|DateTime|Datum/Zeit-Stempel|datetime yyyyMMddHHmmss|
|7|**ItemLedgerEntries / ItemLedgerEntry**||||
|8|EntryNo|Laufende Artikelpostennr.|integer|
|9|ItemNo|Interne Artikel-Nr.|integer|
|10|CustomerItemNo|Kunden Artikel-Nr.|string|
|11|UnitOfMeasure|Einheiten Code|string|
|12|QtyPerUnitOfMeasure|Menge Basiseinheit pro Einheit|integer|
|13|LotNo|Chargennr. auf die sich die Buchung bezieht|string|
|14|EntryTypeCode|Postenart, kodiert<br>0 = Purchase / Einkauf,<br>1 = Sale / Verkauf,<br>2 = Positive Adjmt / Zugang,<br>3 = Negative Adjmt/ Abgang|integer|
|15|EntryType|Postenart, Name|string|
|16|DocumentTypeCode|Belegart, kodiert<br>0 = manuelle Korrektur,<br>1 = Sales Shipment / Verkaufslieferung,<br>3 = Sales Return Receipt / Verkaufsreklamation(Retoure),<br>5 = Purchasereceipt / Einkaufslieferung(Wareneingang),<br>7 = Purchase Return Shipment / EK-Rücklieferung|integer|
|17|DocumentType|Belegart, Name|string|
|18|Description|Buchungsbeschreibung|string|
|19|Quantity|Menge, Zugänge positiver Wert, Abgänge negativer Wert|integer|
|20|PostingDate|Buchungsdatum|date dd.MM.yyyy|
|21|DocumentNo|Interne Belegnummer|string|
|21|ExternalDocumentNo|Externe Belegnummer|string|

</details>

## 2.4. OSTRPT - Auftragsstatus / Order Status (XML)

In den OSTRPT Dateien erhalten Sie die Information über Auftragsstatusänderungen,\
Versandinformationen und Paket-Nr.-Informationen.

Die Dateien haben folgendes Benennungsschema:\
OSTRPT_CustomerOrderNo_StatusCode_YYYYMMDD_HHmmss.xml  

Der Dateiname dient zur Information kann aber nicht sicher ausgewertet werden. 

<details>
<summary>Schemadefinition des OSTRPT-Formats</summary>

  
|   Pos.    |   Name                        |  Description                 |  Data Type (length)  |
|----------:|-------------------------------|------------------------------|----------------------|
|1|**Message**||||
|2|Type                              | Festwert: OSTRPT                  ||
|3|VendorGLN                         | Globale Lokationsnummer           |string (13)|
|4|CustomerGLN                       | Globale Lokationsnummer           |string (13)|
|5|CustomerNo                        | Debitor-Nr.                       |string|
|6|**Status**||||
|7|CustomerOrderNo                   | Kunden Auftrags-Nr                |string|
|8|StatusCode                        | Status-Code - Mögliche Werte:<br>1 = Empfangen,<br>2 = Akzeptiert,<br>3 = Abgelehnt,<br>4 = teilweise geliefert,<br>5 = vollständig geliefert,<br> 6 = Fehler|integer|
|9|StatusDescription                 | Status-Beschreibung               |string|
|10|StatusTimestamp                   | Datum/Zeit-Stempel  |datetime YYYYMMDDHHmmSS|
|11|CorrespondingDocumentType         | Dokumententyp auf den sich der Status bezieht.<br>1 = Auftrag,<br>2 = Lieferschein|integer|
|12|CorrespondingDocumentNo           | Belegnummer                                  |string|
|13|CorrespondingDocumentDate         | Belegdatum YYYYMMDD                    |date YYYYMMDD|
|14|EDIRemoteSystemCode               | Identifiziert das Kundensystem    |string|
|15|**Errors / Error**||||
|16|ErrorMessage                      | Fehlerbeschreibung                |string|
|17|**Shipmentorder**||||
|18|ShippingAgentChanged              | True, wenn der Auftrag mit einem  abweichenden Zusteller versendet wurde.|bool|
|19|OriginShippingAgent               | der ursprüngliche Zusteller       |string|
|20|OriginShippingAgentService        | Interner Service Code             |string|
|21|CustomerShippingAgent             | Identifiziert den Zusteller im externen System   |string|
|22|CustomerShippingAgentService      | Identifiziert die Serviceart im externen System  |string|
|23|**Shipmentorder / Parcel**||||
|24|ParcelNo                          | Paket-Nr.                         |string|
|25|Weight                            | Gewicht                           |decmal|
|26|ShippingAgent                     | Versand-Dienstleister             |string|
|27|ServiceDescription                | Versand-Typ                       |string|
|28|TrackingURL                       | Tracking-URL                      |string|

</details>

## 2.5. RECADV - Wareneingangsmeldung / Inbound Goods Receipt (XML)

Mit diesem Format übertragen wir ihnen gebuchte Wareneingänge und ggf. zugehörige Dokumente (z. B. Lieferschein) oder Bilder der Ware.

Dateiname: WARENEINGANG_*.xml

<details>
<summary>Schemadefinition des RECADV-Formats</summary>

|   Pos.    |   Name                        |  Description                 |  Data Type (length)  |
|----------:|-------------------------------|------------------------------|----------------------|
|1|**PurchaseReceipts / PurchaseReceipt**|||
|2|DocumentType|Festwert: RECADV|||
|3|TransferFlag|0 / 1, Erstsendung / Wiederholung||
|4|WarehouseGLN|Globale Lokationsnummer Logistiker|string (13)|
|5|CustomerNo|Interne Debitor-Nr.|string (20)|
|6|No|Interne ID des geb. Wareneingangs|string (20)|
|7|PurchaseOrderNo|Interne ID der Einkaufsbestellung|string (20)|
|8|ReceivedDate|Wareneingangsdatum|date DD.MM.YY|
|9|YourReference|Referenznummer/-text|string (35)|
|10|**PurchaseReceipt / Customer_Address**|||
|11|No|Interne Debitor-Nr.|string (20)|
|12|CustomerGLN|Globale Lokationsnummer|string (13)|
|13|Name|Firmenname|string (50)|
|14|Name2|Namenszusatz|string (50)|
|15|Address|Adresse (Straße + Hausnr.)|string (50)|
|16|Address2|Adressenzusatz|string (50)|
|17|PostCode|PLZ|string (20)|
|18|City|Ort|string (30)|
|19|CountryRegionCode|Länderkürzel (ISO ALPHA 2)|string (2)|
|20|**PurchaseReceipt / Warehouse_Address**||
|21|ShipToGLN|Globale Lokationsnummer|string (13)|
|22|ShipToName|Empfänger Name, Zeile 1|string (50)|
|23|ShipToName2|Empfänger Name, Zeile 2|string (50)|
|24|ShipToAddress|Adresse (Straße + Hausnr.)|string (50)|
|25|ShipToAddress2|Adressenzusatz|string (50)|
|26|ShipToPostCode|PLZ|string (20)|
|27|ShipToCity|Ort|string (30)|
|28|ShipToCountryRegionCode|Länderkürzel (ISO ALPHA 2)|string (2)|
|29|**PurchaseReceipt / PurchaseLines**|||
|30|PosNo|Positionsnummer|integer|
|31|PurchaseLineNo|Interne Zeilennummer|integer|
|32|ItemNo|Interne Artikel-Nr.|integer|
|33|GTIN|„Global Trade Item Number"|string (13)|
|34|GTINBaseUnitOfMeasure|GTIN der Basiseinheit|string (13)|
|35|CustomerItemNo|Kunden Artikel-Nr.|string (30)|
|36|ItemDescription|Beschreibung 1|string (50)|
|37|ItemDescription2|Beschreibung 2|string (50)|
|38|Quantity|Anzahl für die Position|integer|
|39|UnitOfMeasureCode|Einheit|string (10)|
|40|TotalPieces|Gesamtmenge|integer|
|41|QuantityBase|Menge Basiseinheit|integer|
|42|CustomerOrderNo|Kunden Auftrags-Nr.|string (35)|
|43|CustomerOrderLineNo|Kunden Auftrags-Position|string (20)|
|44|ReturnReasonCode|Rücksendegrund|string (10)|
|45|**PurchaseReceipt / PurchaseLine / ItemTracking / ItemTrackingLine**|||
|46|TrackItemNo|interne Artikelnummer|integer|
|47|TrackCustomerItemNo|Kunden-Artikelnr|string (30)|
|48|TrackItemDescription|Artikelbeschreibung|string (50)|
|49|TrackShipmentLineNo|Lieferscheinzeilennr.|integer|
|50|TrackQuantity|Menge für diese Charge/Seriennummer|integer|
|51|TrackLotNo|Chargennr.|string (20)|
|52|TrackSerialNo|Seriennummer|string (20)|
|53|TrackExpirationDate|Ablaufdatum / MHD|date DD.MM.YYYY|
|54|**PurchaseReceipt / Attachments / Attachment**|||
|55|AttachmentDescription|Dateianlage, Beschreibung|string|
|56|AttachmentName|Dateianlage, Name \*|string|

\* Falls im Wareneingang Dokumente eingescannt oder Bilder von der Ware erstellt wurden,\
befinden sich diese als komprimierte Datei im zip-Format im selben Verzeichnis wie die RECADV-XML-Datei.\
Der Dateiname entspricht dem Feld PurchaseReceiptNo und der Dateiendung .zip.\
Beispiel: EKL123456.zip. Für jede Datei eines Wareneingangs gibt es einen Attachment Eintrag.\
Alle Attachment-Einträge zusammen stellen also das Inhaltsverzeichnis der zip-Datei dar.

</details>

# 3. Importformate / Inbound Messages (CSV)

Zusätzlich zu den XML-Formaten, können wir Aufträge, Artikelstammdaten\
und Wareneingangsmeldungen als CSV- oder Excel-Datei importieren.

**ACHTUNG !**
```
Aktuell migrieren wir unser WMS auf ein neues System.
Dadurch ist diese Dokumentation nicht zu 100% zutreffend und kann nur als Orientierung dienen.
```
**HINWEIS zu Spaltennamen**
Spaltennamen spielen für die Verarbeitung in unserem System keine Rolle.

Sie dienen nur noch zur Orientierung.

Wichtig ist die Position einer Spalte und die Anzahl der übermittelten Spalten.

Diese muss immer der von uns erstellten Konfiguration entsprechen,\
damit die Dateien automatisiert importiert werden können.

## 3.1. PRICAT - Artikelstammdaten / Product Master Data (CSV)

<details>
<summary>Schemadefinition des INVRPT-Formats</summary>

|   Pos.    |   Name                        |  Description                 |  Data Type (length)  |Mandatory|
|----------:|-------------------------------|------------------------------|----------------------|:-------:|
|1| DepositCustomerItemNo            | Artikel-Nr./SKU| string (30)    |x|
|2| Description      | Artikel-Bezeichnung             | string (100) |x|
|3| EAN              | EAN des Produktes                 | string (50)  ||
|4| UnitOfMeasureCode| Artikeleinheitencode, z.B. PCE, PCS | string (20) ||
|5| QtyPerUnitOfMeasure| Anzahl per *UnitOfMeasureCode*    | integer   ||
|6| UnitPrice        | Preis des Einzelproduktes         | decimal      ||
|7| Width            | Breite des Produktes              | decimal      ||
|8| Height           | Höhe des Produktes                | decimal      ||
|9| Length           | Länge des Produktes               | decimal      ||
|10| UnitVolume       | Volumen des Produktes             | decimal      ||
|11| Weight           | Gewicht des Produktes             | decimal      ||
|12| Language         | Sprache der Beschreibung \*     | string (2)   ||
|13| ReorderPoint     | Meldebestand                      | integer      ||
|14| TariffNumber     | Zolltarifnummer                   | string (20)    ||
|15| CountryOfOriginCode| Ursprungsland (ISO ALPHA 2)| string (2)|
|16| SerialNoRequired | Seriennummernpflichtiger Artikel  | string (1), Y/1= Ja, N/0=Nein||
|17| LotNoRequired    | Chargennummerpflichtiger Artikel  | string, Y/1=Ja, N/0=Nein||
|18| ProductCanExpire | Artikel mit MHD/VD | string, Y/1=Ja, N/0=Nein||
|19| Picture|Dateiname oder URL zum Download|string||

\* Wenn der Code DE oder leer ist, wird die Beschreibung als Standard
Artikel-Beschreibung gesetzt. Wenn ein anderer Code verwendet wird, wird
dieser als Übersetzung im Navision angelegt.

</details>

Bei der Auflistung der Felder handelt es sich um die wichtigsten Informationen.\
Weitere Felder, wie z. B. Gebinde und diverse Freifelder, stehen zur verfügung und können bei Bedarf abgestimmt werden.

## 3.2. ORDERS - Aufträge / Sales Order (CSV)

<details>
<summary>Schemadefinition des ORDERS-CSV-Formats</summary>

 |   Pos.    |   Name                        |  Description                 |  Data Type (length)  |Mandatory|
 |----------:|-------------------------------|------------------------------|----------------------|:-------:|
 ||**Felder Auftragskopf, in jeder Zeile zu wiederholen** [mehr...](#aufbau-csv-flat-format)||||
 |1         |CustomerOrderNo                |Ihre Auftrags-Nr.             |string (35)           | X           |
 |2         |PaymentMethodCode              |Zahlungsart                   |string                |             |
 |3         |OrderTotal                     |Auftragswert inkl. MwSt.      |decimal               |             |
 |4         |ShippingAdvise                 |Teil-/Komplettlieferung       |string enum Complete,Partial|       |
 |5         |ExpressOrder                   |Auftrag mit hoher Priorität|string enum           |             |
 |6         |ReferenceText                  |Referenztext, z. B. Bestellnummer ihres Kunden|string (35)|        |
 |7         |LanguageCode                   |Sprachcode des Dokumentes     |string( 10)           |             |
 |8         |CustomerSalesPersonName        |Name des Sachbearbeiters      |string (50)           |             |
 |9         |CustomerSalesPersonPhone       |Telefonnr. Sachbearbeiter     |string (60)           |             |
 |10         |CustomerSalesPersonFax         |Faxnr. Sachbearbeiter         |string (60)           |             |
 |11         |CustomerSalesPersonEmail       |E-Mail Sachbearbeiter         |string (80)           |             |
 |12         |CustomerSalesOrganizationalUnit|Abteilung, Niederlassung etc. |string (50)           |             |
 |13         |OrderedByName                  |Name des Bestellers           |string (30)           |             |
 |14         |OrderedByEmail                 |Email des Bestellers          |string (80)           |             |
 |15         |BillToName                     |Rechnung-An Name, Zeile 1     |string (50)           |             |
 |16         |BillToName2                    |Rechnung-An Name, Zeile 2     |string (50)           |             |
 |17         |BillToContact                  |Rechnung-An Kontakt           |string (50)           |             |
 |18         |BillToAddress                  |Rechnung-An Adresse (Straße + Haus-Nr.)          |string (50)           |             |
 |19         |BillToPostCode                 |Rechnung-An PLZ               |string (20)           |             |
 |20         |BillToCity                     |Rechnung-An Ort               |string (30)           |             |
 |21         |BillToCounty                   |Bei Ländern in denen zutreffend, Bezirk/Landkreis         |string (30)           |             |
 |22         |BillToCountryRegionCode        |Länderkürzel (ISO 3166-2)  |string (2)            |             |
 |23         |ShipToName                     |Liefer-An Name, Zeile 1    |string (50)           | X           |
 |24         |ShipToName2                    |Liefer-An Name, Zeile 2    |string (50)           |             |
 |25         |ShipToContact                  |Liefer-An Kontakt          |string (50)           |             |
 |26         |ShipToAddress                  |Liefer-An Adresse (Straße + Haus-Nr.) [^5] [^6]             |string (50)           | X           |
 |27         |ShipToPostnummer               |Packstation-Nr.            |string (30)           |             |
 |28         |ShipToPostCode                 |Liefer-An PLZ              |string (20)           | X           |
 |29         |ShipToCity                     |Liefer-An Ort               |string (30)           | X           |
 |30         |ShipToCounty                   |Bei Ländern in denen zutreffend, Bezirk/Landkreis         |string (30)           |             |
 |31         |ShipToCountryRegionCode        |Länderkürzel (ISO 3166-2)   |string (2)            | X           |
 |32         |ShipToEmail                    |Email-Adresse des Warenempfängers            |string (80)           |             |
 |34         |ShipToPhoneNo                  |Telefonnummer des Warenempfängers            |string (30)           |             |
 |35         |ShipToTourSequence             |Fahrfolge, interne Verwendung |string (20)           |             |
 |36         |ShipComment                    |Versandsbemerkung             |string                |             |
 |37         |ShippingAgentCode              |Versanddienstleister          |string                |             |
 |38         |ShippingAgentServiceCode       |Versandtyp                    |string                |             |
 |39         |ShipmentDate                   |Warenausgangsdatum         |date, DD.MM.YYYY      |             |
 |40         |InstructionName1                |Handlungsanweisung 1, Name      |string                |            |
 |41         |InstructionName2                |Handlungsanweisung 2, Name      |string                |            |
 |42         |InstructionName3                |Handlungsanweisung 3, Name      |string                |            |
 |43         |AttachmentDescription|PDF-Anhang, Beschreibung      |string                | (X)           |
 |44         |AttachmentPath|PDF-Anhang, Dateiname [mehr...](#zuordnung-von-anhängen-über-dateiname)     |string                | (X)           |
 ||**Felder Auftragszeilen** [^9]|||
 |45         |Type                           |Typ von Produkt               |string enum           |             |
 |46         |CustomerLineNo                 |Auftragsposition              |string (20)           |             |
 |47         |Quantity                       |Menge                         |integer               | X           |
 |48         |DepositCustomerItemNo          |Artikel-Nr. / SKU             |string (30)           | X           |
 |49         |Description1                   |Beschreibung 1                |string (50)           |             |
 |50         |Description2                   |Beschreibung 2                |string (50)           |             |
 |51         |UnitPrice                      |Einzelpreis                   |decimal               |             |
 |52         |QtyPerUnitOfMeasure            |Menge pro Einheit             |integer               |             |
 |53         |UnitOfMeasureCode              |Einheit                       |String (10)           |             |
 |54         |UnitWeight                     |Einzelgewicht                 |decimal               |             |
 |55         |LotNo                          |Chargenummer                  |string (20)           |             |
 |56         |SerialNo                       |Seriennummer                  |string (20)           |             |

</details>

#### Aufbau CSV Flat Format
Es muss für jede Auftragsposition eine Zeile in der CSV Datei vorhanden sein.\
Wenn Sie also einen Auftrag mit 3 Positionen übermitteln wollen,\
müssen in der CSV Datei 3 Zeilen mit denselben Informationen im Bereich des Auftragskopfs (Lieferadresse, Auftrags-Nr., etc.)\
und den jeweiligen Artikelinformationen je Position übermittelt werden.

Alle Zeilen eines Auftrages müssen direkt untereinanderstehen.\
Alle Zeilen eines Auftrages haben den gleichen Wert im Feld CustomerOrderNo.

#### Zuordnung von Anhängen über Dateiname
Anhänge können einem Auftrag auch zugeordnet werden, indem der Dateiname die Auftragsnummer enthällt.\
Beispiel: CustomerOrderNo = 4711, Dateiname = Lieferschein_4711.pdf.\
Wir können unser System entsprechend konfigurieren, dass die Dateien heruntergeladen werden und dann über\
die Auswertung des Dateinamens dem Auftrag zugeordnet werden.\
**Bitte beachten sie unbedingt auch die Anmerkungen (mehr ) unter [1.2.1](#weitere-hinweise-zu-einzelnen-feldern-des-orders-formats)**

## 3.3. PURCHASEORDER - Einkaufsbestellung (Wareneingangsankündigung) / Purchaseorder (Inbound Goods) (CSV)

|   Pos.    |   Name                        |  Description                 |  Data Type (length)  |  Mandatory  |
|----------:|-------------------------------|------------------------------|----------------------|:-----------:|
||**Felder Bestellkopf, in jeder Zeile zu wiederholen**||||
| 1         |CustomerOrderNo                |Ihre Bestell-Nr.              |string (35)           | X           |
|2         |ExpectedReceiptDate            |Wareneingangsdatum            |date, DD.MM.YYYY      |             |
|3         |ReferenceText                  |Referenztext/-nummer          |string (35)           |             |
|4         |VendorShipmentNo               |Lieferscheinrn. Lieferant     |string (35)           |             |
|5         |ShippedFromName                |Lieferant Name, Zeile 1       |string (50)           |             |
|6         |ShippedFromName2               |Lieferant Name, Zeile 2       |string (50)           |             |
|7         |ShippedFromContact             |Lieferant Kontakt             |string (50)           |             |
|8         |ShippedFromAddress             |Lieferant, Straße + Hausnr.   |string (50)           |             |
|9         |ShippedFromPostCode            |Lieferant, Postleitzahl       |string (20)           |             |
|10         |ShippedFromCity                |Lieferant, Ort                |string (30)           |             |
|11         |ShippedFromCounty              |Lieferant, Bezirk/Landkreis   |string (30)           |             |
|12         |ShippedFromCountryRegionCode   |Lieferant, Länderkürzel ISO2  |string (2)            |             |
|13         |ShippedFromEmail               |Lieferant, Email              |string (80)           |             |
|14         |Comment                        |Kommentar                     |string                |             |
|16         |Description                    |Beschreibung der Datei        |string (30)           | X           |
|17         |Path                           |Dateiname                     |string (255)          | X           |
||**Felder Bestellzeilen**||||
|18         |CustomerLineNo                 |Zeilenreferenz Bestellposition|string (20)           |             |
|10         |DepositCustomerItemNo          |Artikelnr. / SKU              |string (30)           | X           |
|20         |Description1                   |Artikelbeschreibung, Zeile 1  |string (50)           |             |
|21         |Description2                   |Artikelbeschreibung, Zeile 2  |string (50)           |             |
|22         |Quantity                       |Menge                         |integer               | X           |
|23         |UnitOfMeasureCode              |Einheit, ggf. Mapping erford. |string (20)           |             |
|24         |QtyPerUnitOfMeasure            |Menge (Basis) pro Einheit     |integer               |             |
|25         |LotNo                          |Chargennummer                 |string (20)           |             |
|26         |SerialNo                       |Seriennummer                  |string (20)           |             |
|27         |ExpirationDate                 |Ablaufdatum/MHD               |date, DD.MM.YYYY      |             |

# 5. Kundenindividuelles Format

Es besteht auch die Möglichkeit abweichende Spaltennamen in der CSV-Datei auszugeben.\
Es ist jedoch zwingend erforderlich,\
dass je Lieferposition immer die vollständigen Auftragskopfdaten (z.B. Auftragsnummer und Lieferanschrift) mit ausgegeben werden.

Die maximalen Feldlängen sind zu beachten.

Beispiel Auftrag:

    Auftragsnummer;Name;Name2;Straße;PLZ;Ort;Land;E-Mail;Artikelnummer;Menge
    A1000;Peter Lustig;;Pusteblumenstraße 1;44444;Löwenstein;peter.lustig@loewenzahn.de;4711;10
    A1000;Peter Lustig;;Pusteblumenstraße 1;44444;Löwenstein;peter.lustig@loewenzahn.de;4712;1
    A1001;Lieschen Müller;;An der Bahn 2;33333;Emmerich;lieschen39@web.de;4711;5
    A1002;Musterfirma;Hans Muster;Mustergasse 1;22222;Musterstadt;AT;4712;100

Beispiel Artikel:

    Artikelnummer;EAN;Artikelbezeichnung;
    4711;4312345678901;Sehr schöner Artikel
    4712;4312345678812;Sehr nützlicher Artikel

# 6. Rückmeldungen (CSV)

Aufgrund des Wechsels auf ein neues WMS können wir nun auch diverse Exporte per CSV anbieten.\
Diese werden zukünftig hier beschrieben.

# 7. Allgemeine Hinweise zur Wartung der Schnittstelle

Die Schnittstelle wird von uns bei Bedarf erweitert.\
D. h. es können neue Formate hinzukommen oder bestehende Formate werden um weitere Felder/Strukturen ergänzt.

Das Entfernen von Feldern wird unter allen Umständen vermieden.\
Sollte dies dennoch notwendig sein, werden wir dies nur geplant und mit entsprechender Vorankündigung tun.

Auf Grund möglicher Erweiterungen empfehlen wir, auf eine strikte Formatprüfung zu verzichten.\
Fragen sie benötigte Daten ab und ignorieren sie Felder, die sie nicht benötigen oder die bisher nicht vorhanden waren.\
So sollte es nicht zu Problemen kommen, wenn wir Erweiterungen an unserer Schnittstelle vornehmen.

# 8. Versionshistorie

|Version    |  Datum   |   Änderungen                 |   Bearbeiter    |
|-----------|----------|------------------------------|-----------------|
| 1.0       |10.05.2016| Ersterstellung               | Ozan Caglayan   |
| 1.1       |03.06.2016| Anpassungen in Datei und Feldern, „Einführung" ergänzt  | Ozan Caglayan   |
| 1.2       |14.12.2016| Ergänzung Packstation        | Ozan Caglayan   |
| 1.3       |26.01.2018| Ergänzung EdiPartnerCode und Remotesystem  | Marco Thyssen   |
| 1.31      |14.09.2018| ORDER, ShipToEmail ergänzt   | Marco Thyssen   |
| 1.4       |16.10.2018| Vollständige Überarbeitung   | Marco Thyssen   |
| 1.41      |19.12.2018| Korrektur Name-Felder        | Marco Thyssen   |
| 1.5       |18.04.2019| Anpassung ORDER, LotNo, SerialNo, LocationCode, BinCode | Marco Thyssen   |
| 1.6       |31.07.2019| Anpassung ORDER, OrderTotal, FullPickOrder, WarehouseCarrier, ReferenceText| Marco Thyssen   |
| 1.7       |07.01.2020| Anpassung ORDER, neues Feld Fahrfolge | Marco Thyssen   |
| 1.8       |23.01.2020| PURCHASEORDER                | Marco Thyssen   |
| 1.9       |10.02.2020| ORDERS, neues Feld ShipToPhoneNo| Marco Thyssen   |
| 2.0       |22.04.2020| ORDERS, neue Felder          | Marco Thyssen   |
| 2.1       |07.10.2020| Neuer Export ITMLEDG, Artikelposten| Marco Thyssen   |
| 2.2       |09.12.2020| Anpassung ORDER, neues Feld Warenausgangsdatum | Marco Thyssen   |
| 2.3       |28.01.2021| Neues Format RECADV, Wareneingang       | Marco Thyssen   |
| 2.4       |03.03.2021| XML und CSV Formate zusammengefasst, Erläuterungen zur Auftragsschnittstelle| Marco Thyssen   |
| 2.5       |22.03.2021| Anpassung OSTRPT, Fehlermeldungen | Marco Thyssen   |
| 2.6       |06.05.2021| Anpassung OSTRPT, weitere Felder für Zusteller und Serviceart   | Marco Thyssen   |
| 2.7       |30.09.2021| ORDERS, ShipToAddress2, Hinweis DHL     | Marco Thyssen   |
| 2.8       |09.11.2021| PRODUCTS, weitere Preisfelder           | Marco Thyssen   |
| 2.9       |28.09.2022| RECADV, ReturnReasonCode, YouReference hinzugefügt| Marco Thyssen   |
| 3.0       |04.10.2022| ORDER, Feld LanguageCode hinzugefügt    | Marco Thyssen   |
| 3.1       |13.01.2023| Anpassung OSTRPT an neues WMS, Wichtige Hinweise zu den CSV-Formaten  | Marco Thyssen   |
| 3.2       |07.03.2023| Anpassung ORDERS und PURCHASEORDERS an das neue WMS        | Marco Thyssen   |

