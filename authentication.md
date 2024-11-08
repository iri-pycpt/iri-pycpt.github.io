---
layout: page
title: "Authentication: downloading protected data"
permalink: /authentication/
---

# Configuring PyCPT for authenticated download of private data

Most of the datasets in the IRI Data Library can be downloaded without logging in, but there are also private datasets that are available only to authorized users.
If you are authorized to use a private dataset, you can configure PyCPT to download private data on your behalf as follows.

1. If you don't already have a Data Library account, create one [here](https://iridl.ldeo.columbia.edu/auth/signup) using an email address and password (don't use the "Sign up with Google/Bitbucket" buttons).
2. Once logged in, visit the Data Library page of the dataset to which you need access. Click on the "Files" tab. You will be taken to an access request form. Fill in and submit the form, and then wait for a member of the Data Library staff to approve your request. While you wait, you can continue with the following steps...
3. Activate your PyCPT conda environment (see the [installation instructions](https://iri-pycpt.github.io/installation/))
4. Run python in that environment.
5. At the python prompt, type ```cptdl.setup_dlauth("email@example.com")```, substituting the email address you used for the Data Library account. Provide your Data Library password when prompted.
6. Exit python (`exit()`)

You will now have a ```~/.pycpt_dlauth``` file, which will be used to authenticate with the IRI data library in future requests using ```use_dlauth=True```
