# gossh

This slim script is forked from https://github.com/robinparisi/ssh-manager.

But added more functions:
  - support sepcific identity_file.
  - support upload/push file to server with scp.
  - support download/pull file from server with scp.
  - support execute remote command from server.
  - remove server alive checker, because it cause some latency.

## Installation

    $ mkdir -p $HOME/bin
    $ cd $HOME/bin
    $ curl https://raw.github.com/yftzeng/gossh/master/gossh -o gossh
    $ chmod +x gossh
    $ hash -r
    $ gossh

File database is named ".gossh".

## Usage

    $ gossh add local:root:localhost:22
    new alias 'local:root:localhost:22' added

    $ gossh add gcos:ant:blog.gcos.me:22:.ssh/id_rsa
    new alias 'gcos:ant:blog.gcos.me:22' added

    $ gossh
    List of availables servers for user ant
    ==============================================
    local	  => root@localhost		  -> 22
    gcos	  => ant@blog.gcos.me	  -> 22	  with .ssh/id_rsa

    Availables commands
    ==============================================
    /home/ant/bin/gossh cc		<alias> [username]		                		connect to server
    /home/ant/bin/gossh add		<alias>:<user>:<host>:[port]:[identity_file]	add new server
    /home/ant/bin/gossh del		<alias>		                			    	delete server
    /home/ant/bin/gossh push	<alias>					                    	upload file to server
    /home/ant/bin/gossh pull	<alias>						                    download file from server
    /home/ant/bin/gossh cmd		<alias>						                    run command on server
    /home/ant/bin/gossh exp								                        export config

    Connect to server
    $ gossh cc gcos

    Push file to server
    $ gossh push gcos bin/gossh

    Pull file from server
    $ gossh pull gcos gossh

    Run command on remote server
    $ gossh cmd gocs ls

## De-installation / Remove

    $ rm -f $HOME/bin/gossh
    $ rm -f $HOME/.gossh

