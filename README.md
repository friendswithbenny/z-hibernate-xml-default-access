# hibernate xml fail

## UPDATE:
Javier solved the mystery in ~5 minutes.

the JPA spec takes pains to define
* default "access" for annotations
* xml facilities to define default "access"

but it does not define:
* default "access" if undefined in xml (without annotations)

therefore my configuration isn't 100% correct,
so this isn't necessarily a hibernate bug.
it wasn't necessarily reasonable to presume un-specified access was possible,
but conversely, note EclipseLink has no problem with this.


## original details:

this is a minimal example of hibernate failing to correctly interpret an xml (non-annotation) mapping.
it includes:
* an annotated persistence unit
* an xml-specified persistence unit

the results are in:

	src/test/java/test.fwb.hibernateXmlFail.TestHibernateXmlFail

it contains:
*	a passing test demonstrating hibernate's failure to build the persistence unit.
*	another passing test to demonstrate that
	hibernate and my configuration are otherwise working,
	as long as the entity in question is annotated.
*	finally, a test configured to use EclipseLink on the xml-mapped bean,
	which passes with flying colors
