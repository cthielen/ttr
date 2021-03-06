# ttr ("Time Tracker")

ttr is a simple command line time tracker.

It organizes time into slips which are placed in timesheets. Timesheets
optionally have a description.

That's it.

## Installation

1. Ensure Ruby is installed correctly. The commands 'ruby', 'irb', and 'gem' should be on your system:

        ruby -v
        ruby 2.0.0p353 (2013-11-22 revision 43784) [x86_64-darwin13.0.0]

2. Ensure the popular package managing gem 'Bundler' is installed:

        gem list bundler

   should return something like 'bundler (1.3.5)'. If the word 'bundler' does not appear, type

        gem install bundler

   to install Bundler.

3. Install tt's dependencies via Bundler:

        bundle install

   If the dependencies fail to install, read the output. ttr uses sqlite3 so you need to
   ensure sqlite3's development files are installed.

4. Build and install the gem to your system:

        rake install

5. You should now have the 'tt' command. If you do not, you're probably missing Ruby's gem binary
   folder from your PATH. Something like the following should help you discover what's missing from
   your PATH:

        gem env | grep "EXECUTABLE DIRECTORY"

## Usage

See 'ttr help' for usage instructions. Here's a scenario:

We want to track time before lunch, stop for lunch, then continue after.

Around 8:00am we type:

    ttr start
    
    Started slip at 2013-12-09 08:00:00 -0800 for timesheet 4

The command returned an ID of '4'. We'll use that. If we forget it, we can always type 'ttr ls' to see
currently open slips.

We'll label this timesheet as 'Monday work':

    ttr desc 4 'Monday work'

Around noon, we stop working:

    ttr stop
    
    Finished slip with 4h 0m 0s for timesheet 4. Total 4h 0m 0s.

After lunch, we'll start another slip on the same timesheet:

    ttr start 4
    
    Started slip at 2013-12-09 13:00:00 -0800 for timesheet 4

At the end of the day:

    ttr stop
    
    Finished slip with 4h 0m 0s for timesheet 4. Total 8h 0m 0s.

And let's see what we did today:

    ttr log
    
    8h 0m 0s 2 slip(s) on timesheet 4 (Monday work)

## Contributing

1. Fork it.
2. Create your feature branch (`git checkout -b my-new-feature`).
3. Commit your changes (`git commit -am 'Add some feature'`).
4. Push to the branch (`git push origin my-new-feature`).
5. Create a new pull request.
