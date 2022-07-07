This will get you the purpose in the privacy policy:
`{{schema.preferencesSchema.fields['privacy.awesomenames_pp'].legalS tatements[screenset.lang].purpose}}`

In the purpose of the privacy policy you can include HTML. Replace the link inside the HREF with the terms of service.:
`I accept the <a target="_blank" href="https://www.google.com/">Terms of Service</a>`

You can put HTML in the label. Example `Welcome to <span style="color:red">your</span>`

## Debugging

No Error Message is Shown on Screens
- Check that the form contains a “Form error” element
- This element is used to display form-level errors

Fields Disappear as Soon as Data is Entered
- This can happen for elements with a “Visible When” attribute 
- Make sure that the “Keep Visible” checkbox is ticked

Any other issues
- Compare to the default screensets and see what they did their.