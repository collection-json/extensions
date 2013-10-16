extensions
==========

Collection+JSON Extensions

This repo contains rought working documents on suggested extensions to the Collection+JSON format. To be included here, an extension MUST NOT introduce any breaking changes to the existing spec. IOW, adding the extension to a response MUST NOT cause any existing (compliant) implementation to break.

## Guidelines ##
Generally, the guidelines for creating extentions are:
 * *Don't Take Away Stuff* : You MUST NOT remove any existing element that is already defined in the Cj documentation.
 * *Don't Redefined Stuff* : You MUST NOT change the meaning or processing rules for any existing element.
 * *All New Stuff is Optional* : Any new element MUST be OPTIONAL. You MUST NOT create a new REQUIRED element in a Cj representation. 

