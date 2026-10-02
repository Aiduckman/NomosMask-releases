# NomosMask releases

Signed and notarized builds of NomosMask, a macOS app that removes personal data from Greek legal documents, entirely offline.

This repository only hosts the release files that the app's «Έλεγχος για ενημερώσεις» button downloads. It contains no source code and no documents.

Requirements: a Mac with Apple Silicon, macOS 14 or later.

## Verifying a manual download

Updates installed through the app's «Έλεγχος για ενημερώσεις» button are checked automatically: each one carries an Ed25519 (EdDSA) signature that the app verifies before it installs, so a tampered update is refused.

If instead you download a `.zip` by hand from the Releases page, that automatic check does not apply. Verify the file yourself before opening it.

1. Compare its SHA-256 against [`SHA256SUMS`](SHA256SUMS) in this repository:

   ```
   shasum -a 256 NomosMask-0.11.0.zip
   ```

   The printed hash must match the line for that file in `SHA256SUMS`. You can also place `SHA256SUMS` next to the download and run `shasum -a 256 -c SHA256SUMS`.

2. After unzipping, confirm the app is notarized by Apple:

   ```
   spctl -a -vvv NomosMask.app
   ```

   It should report `source=Notarized Developer ID`.

---

Υπογεγραμμένες και επικυρωμένες από την Apple εκδόσεις του NomosMask. Εδώ βρίσκονται μόνο τα αρχεία που κατεβάζει το κουμπί «Έλεγχος για ενημερώσεις» της εφαρμογής.

## Έλεγχος αρχείου που κατεβάσατε με το χέρι

Οι ενημερώσεις που εγκαθίστανται από το κουμπί «Έλεγχος για ενημερώσεις» ελέγχονται αυτόματα: κάθε μία φέρει ψηφιακή υπογραφή Ed25519 (EdDSA) που η εφαρμογή επαληθεύει πριν την εγκατάσταση, ώστε μια αλλοιωμένη ενημέρωση να απορρίπτεται.

Αν όμως κατεβάσετε ένα αρχείο `.zip` με το χέρι από τη σελίδα Releases, αυτός ο αυτόματος έλεγχος δεν ισχύει. Επαληθεύστε το αρχείο μόνοι σας πριν το ανοίξετε.

1. Συγκρίνετε το SHA-256 του με το αρχείο [`SHA256SUMS`](SHA256SUMS) αυτού του αποθετηρίου:

   ```
   shasum -a 256 NomosMask-0.11.0.zip
   ```

   Το άθροισμα που εμφανίζεται πρέπει να ταιριάζει με τη γραμμή του αρχείου στο `SHA256SUMS`.

2. Μετά την αποσυμπίεση, επιβεβαιώστε ότι η εφαρμογή είναι επικυρωμένη από την Apple:

   ```
   spctl -a -vvv NomosMask.app
   ```

   Πρέπει να αναφέρει `source=Notarized Developer ID`.
