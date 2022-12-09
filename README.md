# my-bashrc

```bash:.bashrc
# activate_conda
function conda(){
	unset -f conda
	# >>> conda initialize >>>
	# !! Contents within this block are managed by 'conda init' !!
	__conda_setup="$('/home/ohya/anaconda3/bin/conda' 'shell.bash' 'hook' 2> /dev/null)"
	if [ $? -eq 0 ]; then
		eval "$__conda_setup"
	else
		if [ -f "/home/ohya/anaconda3/etc/profile.d/conda.sh" ]; then
			. "/home/ohya/anaconda3/etc/profile.d/conda.sh"
		else
			export PATH="/home/ohya/anaconda3/bin:$PATH"
		fi
	fi
	unset __conda_setup
	# <<< conda initialize <<<
}

# define_direnv
export EDITOR=vi  # select editor
eval "$(direnv hook bash)"
alias da='direnv allow'

# docker_exec_alias
function de() {
  CONTAINER="$1"
  docker exec -it $CONTAINER bash
}

# display_capture_commands
function cap() {
  printf 'record:
  [full] Alt + Ctrl + Shift + R
  $ gsettings set org.gnome.settings-daemon.plugins.media-keys max-screencast-length 3600
capture:
  [full] PrtScr
  [actv] Alt + PrtScr
  [rect] Shift + PrtScr
  Press "Ctrl" while taking a screenshot to copy to clipboard and avoid saving.\n'
}
```
