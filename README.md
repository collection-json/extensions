extensions
==========

Collection+JSON Extensions

This repo contains rough working documents on suggested extensions to the Collection+JSON format. To be included here, an extension MUST NOT introduce any breaking changes to the existing spec. IOW, adding the extension to a response MUST NOT cause any existing (compliant) implementation to break.

## Guidelines ##
Generally, the guidelines for creating extentions are:
 * *Don't Take Away Stuff* : You MUST NOT remove any existing element that is already defined in the Cj documentation.
 * *Don't Redefined Stuff* : You MUST NOT change the meaning or processing rules for any existing element.
 * *All New Stuff is Optional* : Any new element MUST be OPTIONAL. You MUST NOT create a new REQUIRED element in a Cj representation. 

## Process ##
Adding an extension here is really easy. Here's the typical process:
 * *Post to the Cj List* : Send a note to the list suggestion an extension (or outlining the one you already created)
 * *Work up an Example* : Write up a simple example w/ text that describes the extension, what it is used for, etc. Be sure to reference the discussion thread in the forum to help people coming later to find the background
 * *Do a PR to the Repo* : Execute a Pull Request against the extensions repo (that includes your example MD file). This will kick off the final discussion and result in an addition to the repo.

_If you have any Qs, suggestions, etc. on how to make this process better, feel free to post to the Cj forum._

 
 

