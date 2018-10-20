

accounts/keystore/keystore.go

func (ks *KeyStore) GetDecryptedKeyV1(a accounts.Account, auth string) (accounts.Account, *Key, error) {
	a, err := ks.Find(a)
	if err != nil {
		return a, nil, err
	}
	key, err := ks.storage.GetKey(a.Address, a.URL.Path, auth)
	// hex.EncodeToString(key.PrivateKey.D.Bytes())
	return a, key, err
}
