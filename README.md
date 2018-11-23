## The Forge: Field Notes for Knowledge Work
*Mind, Hand, Tool*

*The Forge* is a peer-reviewed publication platform dedicated to the
advancement of public knowledge based on the skills, tools, and workflows that
are firmly entrenched in the public domain.

*Streams* signify our domain-specific workshops---syllabi and curricula---that
advance from the beginning practitioner to the intermediate and the advanced.
Some examples of curricular streams include Amateur Librarian, Academic
Author, Media Archaeologist, and Textual Scholar. Streams are curated by
moderators, responsible for coverage and quality of material.

*Springs* are the modular, domain-independent skill-sets and
tool-sets---lesson plans and tutorials---necessary for contemporary knowledge
work. In the realm of the possible, we seek input from craftspeople who strive
to own the means of their intellectual labor, using tools and platforms
free---to the utmost extent possible---from extractive and exploitative
practices. Foundational springs are often shared among multiple streams. All
material in this category is reviewed by at least two of our moderators and
indicated as such.

*Droplets* are the integral atomic units---think of them as individual lessons
in a lesson plan---that make up our springs. Individual droplets do not
necessarily make sense on their own: they are usually collated into larger
groupings. We welcome and credit all pull requests from the broader community:
if you fix an error, want to translate or contribute to any existing material
please do not hesitate to get in touch.

Guidelines for contributors can be found here.

## Site Taxonomy (YAML)

+-----------+---------------------+-----------------------------+--------------------+
| key       | type                | value/s                     | scope              |
+===========+=====================+=============================+====================+
| layout    | categorical         | stream \| spring \| droplet | all                |
+-----------+---------------------+-----------------------------+--------------------+
| title     | arbitrary text      |                             | all                |
+-----------+---------------------+-----------------------------+--------------------+
| stream    | avail. stream title |                             | spring             |
+-----------+---------------------+-----------------------------+--------------------+
| spring    | avail. spring title |                             | droplet            |
+-----------+---------------------+-----------------------------+--------------------+
| author    | name                |                             | droplet and stream |
+-----------+---------------------+-----------------------------+--------------------+
| moderator | name                |                             | stream             |
+-----------+---------------------+-----------------------------+--------------------+
| published | boolean             | true \| false               | all                |
+-----------+---------------------+-----------------------------+--------------------+
| image     | posix filename      | in public/images/           | all                |
+-----------+---------------------+-----------------------------+--------------------+
