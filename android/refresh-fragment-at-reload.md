
# Refesh fragment at reload

If you want to **refresh the fragment contents upon db update**

If so, detach the fragment and reattach it

```java
// Reload current fragment
Fragment fragment = getSupportFragmentManager().findFragmentByTag("Your_Fragment_TAG");
if (fragment != null) {
    FragmentTransaction fragTransaction = getSupportFragmentManager().beginTransaction();
    fragTransaction.detach(fragment);
    fragTransaction.attach(fragment);
    fragTransaction.commit();
}
```

`Your_Fragment_TAG` is the name you gave your fragment when you created it

This code is for support library.

If you're not supporting older devices, just use `getFragmentManager` instead of `getSupportFragmentManager`

In case you **do not have the fragment tag**, the following code works well

```java
// Reload current fragment
Fragment currentFragment = getActivity().getFragmentManager().findFragmentById(R.id.fragment_container);
if (currentFragment instanceof "NAME OF YOUR FRAGMENT CLASS") {
    FragmentTransaction fragTransaction = (getActivity()).getFragmentManager().beginTransaction();
    fragTransaction.detach(currentFragment);
    fragTransaction.attach(currentFragment);
    fragTransaction.commit();}
}
```

### Refresh fragment is not working any more?

Some optimizations were added to Fragment Transactions in Revision 25.1.1 of the Support Library. (see [https://developer.android.com/topic/libraries/support-library/revisions.html#25-1-1](https://developer.android.com/topic/libraries/support-library/revisions.html#25-1-1)). Disabling those for your transaction will make it work as expected:

```java
// Reload current fragment with disabling optimizations
Fragment fragment = getSupportFragmentManager().findFragmentByTag("Your_Fragment_TAG");
if (fragment != null) {
    FragmentTransaction fragTransaction = getSupportFragmentManager().beginTransaction();
    fragTransaction.setAllowOptimization(false);
    fragTransaction.detach(fragment).attach(fragment).commitAllowingStateLoss();
}
```

**Update**

`setAllowOptimization` is deprecated. Use `setReorderingAllowed` instead.

</br>

## References

1. [https://stackoverflow.com/questions/20702333/refresh-fragment-at-reload/20702418](https://stackoverflow.com/questions/20702333/refresh-fragment-at-reload/20702418)
2. [https://stackoverflow.com/questions/41270858/refresh-fragment-is-not-working-any-more](https://stackoverflow.com/questions/41270858/refresh-fragment-is-not-working-any-more)