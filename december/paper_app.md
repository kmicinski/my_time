My Paper tracking app
=====================

The goal of this app is to make organizing and scheduling my reading a
pleasant experience.

Allows papers to be organized into categories:
- Contracts,
- Higher order,
- etc...,
- In reality these are all just tags.

The main screen will have a collection of categories, drop down
categories that open links to papers. But this won’t mean anything,
there can also be ad hoc structure, so I can organize by publication
date, category, tag, etc...

Common problems I have
----------------------

1. What papers cite and are cited by this?
2. What other work is there on this topic?
3. What is this author's research area?
4. Can I browse all of the POPL publications ever?


Querying
--------

The main page when you open the app will be a page to query sets of
papers based on a formula: the app will then solve for the set of
objects that match the conjunction of this formula.

Also, there will be a link at the top right to add a paper.

When I want to query papers, I form a query which represents a
conjunction.

The main screen has a sort of AJAX-y thing which allows papers to be
queried by category, allows you to type a tag, date, author, etc.

What is a paper
---------------

- The baseline content, stored in PDF.  (And *nothing* else, if it's
  .ps, I'll have the backend run a script to convert it to pdf.)

- This will be stored as a file, the table of the database will simply
  hold a link to this.

  + This might be obvious, but I don't want to be constantly making
  these large queries and then also shipping the entire content of the
  papers across the network at each time.

  + Same thing for comments, I think.
  
- Some unique identifier, usually I store these in the papers.

- Set of extensible identifiers called tags.

- A set of authors.

- Authors should be fairly unqiue, should there be a table identifying
  authors.

  + How to identify authors?  Simply a string representing their first
  and last names?  What about Simon P. Jones?
  + A list of names.

  + The software should be able to easily disambiguate and recommend
  authors that someone might be. 
  
  + Implies all authors will simply be unique IDs and there will be
  mappings of string lists which regard as the same author.
  
  + I can link these authors to a webpage, Google Scholar profile,
  etc..	  

  + Which allows me to find newest papers by these authors on an alert
  basis.

- Problem 3 implies that authors should be somehow extensible, so
  that I can add information about their publication records.


Following Conferences
---------------------

Problem 4 implies that I should somehow be able to follow conferences,
I'm not sure how this will be possible, because it seems like there's
no standard syndication format for the different programs.

Linking to other profiles
-------------------------

Link to Google Scholar in some way, I assume they have some sort of
API, but I'm not sure what it is: in the worst case scenario, I can
probably simply use XPath, right...?

Assembling BibTeX entries
-------------------------

Also a great feature, at any time I can just get a database, by going
to the controller, and a side page: app/masterbibtex.bib.

(This also supports querying based on the main page, meaning that the
app will have a way to query simply over a set of papers.)

Viewing a paper
---------------

I'd like to use a similar strategy to the one that Matt described for
actually viewing papers and making comments on them.

Each paper has a set of notes associated with it: 

- These notes are kept in the form of LaTeX based text, along with
  inference rules.  How can I render this: Pandoc?

- I think I still learn best by copying the paper down in a journal
  next to it, but only as disposable paper that I use for thinking in
  the small.

I want to code this up as a rails app.  Initially, I want to have
papers in categories, along with notes that I can take on the papers.

I want to use pdf.js to view the papers and make notes on them.  I'd
like to be able to be able to write the following:

- Annotations on individual sections of the paper.

- Summaries for each of the papers, notes that I can make up for
  things, summaries of the papers.

  + Writing notes allows me to concretize my thinking and make sure I
  understand what's going on in each paper.

  + Also essential: being able to write up examples for each paper.
  How can this work?  I don't know what "examples" look like a priori?

- 
