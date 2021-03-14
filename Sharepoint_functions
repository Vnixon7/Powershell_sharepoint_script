
#upload a file to sharepoint
function send-spfiles([parameter(Mandatory)]$Sharepoint_url,[parameter(Mandatory)]$Local_files_path, [parameter(Mandatory)]$Upload_folder) {
    Set-ExecutionPolicy -Scope CurrentUser Unrestricted
    Connect-PnPOnline -Url $Sharepoint_url -UseWebLogin
    try{
        $Files = Get-ChildItem $Local_files_path
    }
    catch{
        "An error occured......."
          "Check your paths for errors"
          "There may not be files in listed folder"
        }
    foreach($File in $Files){
        #$File = $Files[0]
        Add-PnPFile -Folder $Upload_folder -Path $File.FullName
  }
  "Upload Complete!"
  Disconnect-PnPOnline
}

#download a file from sharepoint
function get-spfiles ([parameter(mandatory)]$Sharepoint_url,[parameter(mandatory)]$Sharepoint_folder,[parameter(mandatory)]$Download_folder_path){
    Set-ExecutionPolicy -Scope CurrentUser Unrestricted
    Connect-PnPOnline -Url $Sharepoint_url -UseWebLogin
    try {
        $files = Get-PnPFolderItem -FolderSiteRelativeUrl $Sharepoint_folder -ItemType File
    }
    catch {
           "An error occured......."
           "Check your paths for errors"
           "There may not be files in listed sharepoint folder"
        }

    foreach($file in $files){
        Get-PnPFile -Url $file.ServerRelativeUrl -Path $Download_folder_path -Filename $file.Name -AsFile
    }
    "Download Complete!"
    Disconnect-PnPOnline
}
