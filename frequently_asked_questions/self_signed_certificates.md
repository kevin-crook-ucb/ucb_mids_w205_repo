# Moved to bCourses - all of the content in this page has been moved to bCourses, and as of April 15, 2022, is no longer being updated.  Please use bCourses for the most recent, up to date version. This repo will be deleted once we are sure we have moved everything to bCourses correctly.

# Self Signed Certificates - FAQ - Frequently Asked Questions

## What is the purpose of security certificates?

Security certificates serve two main purposes:

1) Verify identity of a server
2) Encrypt network traffice between you and the server

## What is the difference between a certificate issues by an official Certificate Authority (CA) and a self-signed certificate?

A certificate from a CA handles both 1 (identity verification) and 2 (encryption).

A self-signed certificate handles only 2 (encryption).

## Can't we just run unencrypted and skip the hassles of the self-signed certificates?

If we run encrypted anyone can easily login to the Jupyter Notebook server, create a Jupyter Notebook, write code to install their own public key, login using their public key, and use sudo to gain root access.

There are bots that do nothing but scan IP addresses and ports looking for unencrypted connections to exploit.

## At work we use self-signed certificates all the time, yet never receive security warnings?

Your work has probably setup a PKI (private key infrastructure) that issues certificates.  All browsers have been configured to allow certificates from the PKI. 

## Can we setup a PKI for our VM?

Yes, but it requires an advanced knowledge of how to setup, configure, and run a PKI, which is well above the scope of w205. The skill set is that of a very advanced Linux system engineer who is well versed in cryptography, typically with several years of Linux system engineering experience.

