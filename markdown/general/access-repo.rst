Using the access repo
=====================

All our passwords are stored in public gpg encrypted files in the
`access <https://github.com/atom-robotics-lab/access>`__ repository. The
access repo above utilizes something called `gpg <https://gnupg.org/>`__
to encrypt and decrypt the passwords.

If you have already uploaded your gpg key to keys.openpgp.org then you
can skip the primer section.

GPG ,a primer
-------------

GPG stands for GNU Privacy Guard. It basically uses two set of keys, a
public key and a private key. These two keys are linked together. If I
encrypt something with your public key then only you would be able to
decrypt it with your private key. As the name implies a public key is
something that can be shared with the public, whereas the private key
should be kept secret.

How to get yourself a gpg key
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

First install gpg

.. code:: shell

   sudo apt update 
   sudo apt install gnupg2

Now generate the key

.. code:: shell


   gpg --gen-key

After this command follow the prompts and answer all the questions it
asks you. Post this, you will have generated a gpg private and public
key.

Use

.. code:: shell


   gpg --list-keys

Uploading this key
~~~~~~~~~~~~~~~~~~

Now that you have generated this key you need to upload it to a
keyserver so others can discover and use it.

Step 1
^^^^^^

Export your public key

.. code:: shell

   cd ~
   gpg --export --armor > public.txt 

Step 2
^^^^^^

Now head `here <https://keys.openpgp.org/upload>`__ and upload the
public.txt file which you just generated which must be in your home
directory

You will then be prompted to verify your email, complete this step and
you’ll be done.

Setting up gopass and access repo
---------------------------------

gopass is the tool we use which further uses gpg to encrypt and decrypt
the passwords

-  Install and setup `gopass <https://www.gopass.pw/#install>`__

Cloning the access repository
-----------------------------

.. code:: shell

   gopass clone https://github.com/atom-robotics-lab/access

Now that you have cloned the repository, run gopass list to see the
various accounts.

To view a password in plain text, run

.. code:: shell


   gopass show <name of secret>

Running this would ask you your gpg password which you entered while
creating your gpg key. If you don’t have access to the secrets, then you
would get an error.
