# Part4_FetchingValueWithSpecificAttribute

In this part, we'll display Invoice Issuer and Invoice Receiver parties' informations.

By the time we try to apply the above sentence, there will be usage of '<xsl:if>' 
We will print node of 'ID's  'schemeID' attribute if and only if the value of it is equal to 'TaxID'.

There is also 'BranchID' value but it will not be printed out.

This invoking 'TaxID' value can be seen in the following code snippet.

<xsl:for-each select="./PartyIdentification">
	<xsl:if test= "./ID/@schemeID = 'TaxID'">
		<xsl:value-of select="."/>
	</xsl:if>
</xsl:for-each>	

I also pointed out the value to be printed in XML file. It is written in red in image1.PNG.

The result can be seen in output.html file.