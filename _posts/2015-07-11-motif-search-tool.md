---
layout:     post
title:      Protein Motif Search Tool
date:       2017-11-25
summary:    Motif Search Tool implemented on the web using Python, JavaScript and HTML.
categories: jekyll pixyll
---
## Background

During a final year module at university, I was tasked to produce an application that biologists could use to search amyloid protein sequences for a specific pattern that is known to cause neurodegenerative  diseases such as Alzheimer's disease.


The design decided upon was a website based application, which in my opinion is much better suited to the intended audience. The front-end website would deal with all the user input options whilst keeping a clean and minimalist design to ensure accessibility for all levels of technical literacy. The backend of the service consisted of a Python script that would perform some operations on the users inputted value, and then feed the results back to the HTML document for the user to view.


Due to limitations on the school webserver, modern Python libraries and frameworks were not used. Instead, to run python from the web, CGI (Common Gateway Interface) was used. The CGI script written in Python would be invoked by the HTTP server and would then process data fed through the HTML forms on the web front-end.

## Implementation
The following code highlights how the linear motifs were found in the given sequence number. The basis of the function was a text mining task, utilising a regex pattern which was converted from the given prosite pattern.
{% highlight python %}
  def get_linear_motifs(sequence):
    innerList = [] # Creation of new list to house the motifs found
    # Stores all the sequences found that match the regex given
    iterObject =
    re.finditer(r"(?=([^P][^PKRHW][VLSWFNQ][ILTYWFN][FIY][^PKRH]))",
     sequence)

    # Loops through the iterator then constructs a string
    for match in iterObject:
        run_start = match.start()+1
        run_end = match.end()+6 # Sequence always 6 characters long
        #Appends each of the matches found to the Dictionary
        innerList.append({'start_pos': str(run_start),
         'sequence_found' : match.group(1),
          'end_pos' : str(run_end)})

    # Appends the list populated above to the output data
    outputData['success_data'].append({'motifs_found': innerList})
{% endhighlight %}

The website facilitates several input options, inlucing a single protein search and a batch protein search. This was achieved using multiple functions with differing techniques of splitting up inputted queries. Batch queries were incrementally run through the Uniprot API and then output was provided to the user once all queries were complete.

## Work Produced
The final product is highlighted in the images below:
<img src="{{ site.url }}{{  site.baseurl }}/images/motif/motif-frontpage.png" alt="An image of Keele hall as a placeholder">