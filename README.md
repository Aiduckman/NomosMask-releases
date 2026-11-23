# NomosMask releases

Signed and notarized builds of NomosMask, a macOS app that removes personal data from Greek legal documents, entirely offline.

This repository only hosts the release files that the app's «Έλεγχος για ενημερώσεις» button downloads. It contains no source code and no documents.

Requirements: a Mac with Apple Silicon, macOS 14 or later.

Besides the update check, the app sends feedback only when you press send. What is sent is the text you write, the type of report you choose, the app version and the macOS version, and, only if you add them, a page number and a contact e-mail address.

## Verifying a manual download

Updates installed through the app's «Έλεγχος για ενημερώσεις» button are checked automatically: each one carries an Ed25519 (EdDSA) signature that the app verifies before it installs, so a tampered update is refused.

If instead you download a `.zip` by hand from the Releases page, that automatic check does not apply. Verify the file yourself before opening it.

1. Compare its SHA-256 against [`SHA256SUMS`](SHA256SUMS) in this repository:

   ```
   shasum -a 256 NomosMask-0.17.0.zip
   ```

   The printed hash must match the line for that file in `SHA256SUMS`. You can also place `SHA256SUMS` next to the download and run `shasum -a 256 -c --ignore-missing SHA256SUMS`.

2. After unzipping, confirm the app is notarized by Apple and correctly signed:

   ```
   spctl -a -vvv NomosMask.app
   codesign --verify --deep --strict --verbose=2 NomosMask.app
   ```

   `spctl` should report `source=Notarized Developer ID` and an `origin=` line that reads `origin=Developer ID Application: Georgios Veroiotis (5J4ZZ499X5)`. If the name or the team ID (5J4ZZ499X5) is different, do not open the app. `codesign` should print no error.

---

Υπογεγραμμένες και επικυρωμένες από την Apple εκδόσεις του NomosMask. Εδώ βρίσκονται μόνο τα αρχεία που κατεβάζει το κουμπί «Έλεγχος για ενημερώσεις» της εφαρμογής.

Εκτός από τον έλεγχο ενημερώσεων, η εφαρμογή στέλνει σχόλια μόνο όταν πατήσετε αποστολή. Αποστέλλονται το κείμενο που γράφετε εσείς, ο τύπος της αναφοράς που επιλέγετε, η έκδοση της εφαρμογής και η έκδοση του macOS και, μόνο αν τα προσθέσετε, ένας αριθμός σελίδας και μια διεύθυνση e-mail επικοινωνίας.

## Έλεγχος αρχείου που κατεβάσατε με το χέρι

Οι ενημερώσεις που εγκαθίστανται από το κουμπί «Έλεγχος για ενημερώσεις» ελέγχονται αυτόματα: κάθε μία φέρει ψηφιακή υπογραφή Ed25519 (EdDSA) που η εφαρμογή επαληθεύει πριν την εγκατάσταση, ώστε μια αλλοιωμένη ενημέρωση να απορρίπτεται.

Αν όμως κατεβάσετε ένα αρχείο `.zip` με το χέρι από τη σελίδα Releases, αυτός ο αυτόματος έλεγχος δεν ισχύει. Επαληθεύστε το αρχείο μόνοι σας πριν το ανοίξετε.

1. Συγκρίνετε το SHA-256 του με το αρχείο [`SHA256SUMS`](SHA256SUMS) αυτού του αποθετηρίου:

   ```
   shasum -a 256 NomosMask-0.17.0.zip
   ```

   Το άθροισμα που εμφανίζεται πρέπει να ταιριάζει με τη γραμμή του αρχείου στο `SHA256SUMS`. Μπορείτε επίσης να βάλετε το `SHA256SUMS` δίπλα στο αρχείο και να εκτελέσετε `shasum -a 256 -c --ignore-missing SHA256SUMS`.

2. Μετά την αποσυμπίεση, επιβεβαιώστε ότι η εφαρμογή είναι επικυρωμένη από την Apple και σωστά υπογεγραμμένη:

   ```
   spctl -a -vvv NomosMask.app
   codesign --verify --deep --strict --verbose=2 NomosMask.app
   ```

   Το `spctl` πρέπει να αναφέρει `source=Notarized Developer ID` και μια γραμμή `origin=` που γράφει `origin=Developer ID Application: Georgios Veroiotis (5J4ZZ499X5)`. Αν το όνομα ή το αναγνωριστικό ομάδας (5J4ZZ499X5) είναι διαφορετικό, μην ανοίξετε την εφαρμογή. Το `codesign` δεν πρέπει να εμφανίσει σφάλμα.
