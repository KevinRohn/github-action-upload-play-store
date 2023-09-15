# :package: GitHub Action `Upload Android App Bundle to Google Play Store`

> A GitHub Action to upload an Android App Bundle (.aab file) to the Google Play Store using the Play Developer API.

## :question: Why use this GitHub Action?

Uploading an Android App Bundle (.aab) to the Google Play Store is an essential step in the Android development process. Doing this manually can be time-consuming and error-prone, especially for CI/CD pipelines. This GitHub Action automates the upload process using the Play Developer API, making it convenient and reliable.

## About

This action allows you to automatically upload an Android App Bundle to the Google Play Store. You can specify various parameters like the package name, track for the release, and release status. It supports both public and private repositories.

## Usage

>:white_flag: See the [inputs](#inputs) section for detailed descriptions.

```yaml
- name: Upload Android App Bundle to Google Play Store
  id: upload_aab
  uses: KevinRohn/github-action-upload-play-store@v1.0.0
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
  uses: KevinRohn/github-action-upload-play-store@v1.0.0
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
  uses: KevinRohn/github-action-upload-play-store@v1.0.0
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