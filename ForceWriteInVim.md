File was opened in READ-ONLY, do modification and write it anyway:
:w !sudo tee %

:w --> write
!sudo --> call sudo
tee --> execute tee (read from standard input and write to standard output and files)
% --> use current file name to save
