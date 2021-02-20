# Part4_FetchingValueWithSpecificAttribute

In this part, we'll display Invoice Issuer and Invoice Receiver parties' informations.

And whilst applying the above sentence, there will be usage of `<xsl:if>` 

Below is related part of xml file. 

There are two types of ID tags inside `<PartyIdentification>` tag and I want to reach and print only the one having TaxID attribute.
```
	<AccountingSupplierParty>
		<Party>
			<Name>Safedrive Logistics</Name>
			<PostalAddress>
				<StreetName>Atatürk Caddesi</StreetName>
				<CitySubdivisionName>Beşiktaş</CitySubdivisionName>
				<CityName>İstanbul</CityName>
				<Country>Turkey</Country>
			</PostalAddress>
			<TaxScheme>
				<Name>İstanbul Tax Office</Name>
			</TaxScheme>
			<PartyIdentification>
				<ID schemeID="BranchID">0120120125</ID>
			</PartyIdentification>
			<PartyIdentification>
				<ID schemeID="TaxID">1110002225</ID>
			</PartyIdentification>
		</Party>
	</AccountingSupplierParty>
```
So, in order to do that, I should parse all PartyIdentification tags with for-each keyword. 
Then, if there is some specific attribute(@schemeID) with specific value (TaxID) located under PartyIdentification's hiearchy (i.e. ID tag), I could print the value of this ID node with `<xsl:value-of select="."/>` 
	
``` 
<xsl:for-each select="./PartyIdentification">
	<xsl:if test= "./ID/@schemeID = 'TaxID'">
		<xsl:value-of select="."/>
	</xsl:if>
</xsl:for-each>	
```
