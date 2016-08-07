Moodle Stoa on OpenShift
========================

This git repository helps you get up and running a version of Moodle
developed by the USP such as Moodle Stoa (http://disciplinas.stoa.usp.br)
on OpenShift. This application does not use the original version developed by
the group atp.usp.br, it optains the source code from the repository
https://git.uspdigital.usp.br/6655440/moodle with a set of new features and
plugins developed by the CAED group (http://caed-lab.com). 

Running Moodle Stoa on OpenShift
----------------------------

Create an account at https://www.openshift.com and install the client tools (run 'rhc setup' first)

Create a php-5.4 application (you can call your application whatever you want)

        rhc app-create your_app_name php-5.4 mysql-5.5
        cd your_app_name
	git remote add github -f https://github.com/geiser/openshift-moodle.git
        git merge github/master -s recursive
        git push origin master

That's it, you can now checkout your application at:

	http://your_app_name-$your_namespace.rhcloud.com


Notes
=====
The default branch use is stoa29 (Moodle Stoa). You can change the branch in the
file: GIT_ROOT/.openshift/action_hooks/deploy

GIT_ROOT/.openshift/action_hooks/deploy:
    This script is executed with every 'git push'.  Feel free to modify this script
    to learn how to use it to your advantage.  By default, this script will create
    the database tables that this example uses.

    If you need to modify the schema, you could create a file
    GIT_ROOT/.openshift/action_hooks/alter.sql and then use
    GIT_ROOT/.openshift/action_hooks/deploy to execute that script (make sure to
    back up your application + database w/ 'rhc app snapshot save' first :) )

