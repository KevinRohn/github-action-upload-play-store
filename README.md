# Upload to Google Play Store

> GitHub Action for uploading Android App Bundles (.aab) to the Google Play Store using the Play Developer API.

Automates the upload process in your CI/CD pipeline, eliminating manual uploads through the Play Console. 
Supports all release tracks (internal, alpha, beta, production) and release statuses (draft, completed, halted, inProgress).

## Usage

>:white_flag: See the [inputs](#inputs) section for detailed descriptions.

```yaml
- name: Upload Android App Bundle to Google Play Store
  id: upload_aab
  uses: KevinRohn/github-action-upload-play-store@v1.0.2
  with:
    service_account_json: ${{ secrets.SERVICE_ACCOUNT_JSON }}
    package_name: "com.example.myapp"
    aab_file_path: "./build/outputs/bundle/release/app-release.aab"
    track: "internal"
    release_status: "draft"
```

## Usage Examples

### Upload an Android App Bundle to the internal track with draft status

```yaml
- name: Upload .aab to Internal Track
  id: upload_internal
  uses: KevinRohn/github-action-upload-play-store@v1.0.2
  with:
    service_account_json: ${{ secrets.SERVICE_ACCOUNT_JSON }}
    package_name: "com.example.myapp"
    aab_file_path: "./build/outputs/bundle/release/app-release.aab"
    track: "internal"
    release_status: "draft"
```

### Upload an Android App Bundle to the production track with completed status

```yaml
- name: Upload .aab to Production Track
  id: upload_production
  uses: KevinRohn/github-action-upload-play-store@v1.0.2
  with:
    service_account_json: ${{ secrets.SERVICE_ACCOUNT_JSON }}
    package_name: "com.example.myapp"
    aab_file_path: "./build/outputs/bundle/release/app-release.aab"
    track: "production"
    release_status: "completed"
```

## Inputs

The action supports the following inputs:

- `service_account_json`  
  Base64 encoded service account JSON key for Google Cloud with access to the Play Developer API.  
  **Required:** *true*

- `package_name`  
  Android package name as defined in `AndroidManifest.xml`.  
  **Required:** *true*

- `aab_file_path`  
  File path to the Android App Bundle (.aab) you wish to upload.  
  **Required:** *true*

- `track`  
  The track where you want to upload the `.aab` file. Available options: `internal`, `alpha`, `beta`, `production`, `rollout`.  
  **Required:** *true*

- `release_status`  
  Release status of the app. Available options: `draft`, `completed`, `halted`, `inProgress`.  
  **Required:** *true*

## Outputs

The action does not produce any outputs at the moment. Successful execution will print a success message in the workflow logs.

## Support

Feel free to contribute to the action's development or report issues on the GitHub repository.