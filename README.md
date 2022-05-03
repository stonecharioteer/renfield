# Renfield

Renfield is a tool I am writing in order to syncronize multiple cheap external
hard drives and maintain an easily accessible database that 

## Why does this exist?

I've been meaning to build a NAS for all the wrong reasons. I wanted to have backups
of my media collection, movies, shows you cannot find online, home videos and photos.
I'm based out of India, where NAS-grade Hard Drives are ridiculously expensive. Importing
them is not an option either, especially not for a personal NAS that I have to maintain
myself.

My options were:

1. Get a low-end NAS that I could use with drives that I *can* afford here.
   This would mean buying 1TB to 2TB hard drives, probably Seagate IronWolf or
   WD Red, both of which are higher priced in India than they are in the US,
   and hoping they don't die every few months.
2. Build a NAS myself, involving assembling the computer, getting a hardware
   RAID controller, dealing with the NAS OS installation and maintainance.

I don't want to do the first because the commercial NAS boxes *suck*. And I
don't want to do the second because while it's fun to maintain servers, it's not
fun when they go down and you have to debug them.

I needed a solution that would help me achieve the bare minimum of what I want.
I wanted storage that I can reach over the local network so I can stream video
to my smart TV. I also wanted backups so when the hard drives fail, I don't need
to go down the `e2fck` rabbithole. I've been there. It's dark.

So after speaking with [a friend](), I realized that the more practical solution
would be to buy *cheap* external hard drives, and *lots* of them. The most
cost-efficient drives are the 4TB segment, at least here in India. I plan on
buying a couple of them every few months to grow out my collection, *and* to
grow out the backups.

But actually performing these backups and keeping track of what's where is a
nightmarish task. You'd need not only to maintain a list of your files in a
central database, you'd also need to syncronize the changes, *not* just in the
files themselves but even on the event of changing the file path or name.

My goals with Renfield are simple:

1. Maintain a database of files, metadata (hashes, path(s), present and previous
   filenames).
2. Label drives in the database so that they're marked to be synchronized.
3. Account for off-database changes in the system (renames, new files etc).
4. Synchronize file changes between connected drives when they're copied. This
   needs to be 2 way, recognizing which is a newer version, and not just relying
   on some drive to be marked as primary or secondary.
5. For those drives that are marked as NAS drives, maintain the drive health
   statistics.

I want to keep things simple. Renfield should write all the data into a sqlite
database at first, and eventually I should figure out a way to use either
postgres or maybe a NoSQL db on the cloud.

## Why the Name?

Renfield is the name of Count Dracula's [deranged, fanatically devoted servant
and *familiar*.](https://en.wikipedia.org/wiki/Renfield). I figured any tool I
build needs to not only be resilient, but also very, *very*, **very** thorough;
just like Renfield was in helping Dracula with his *exploits*.
