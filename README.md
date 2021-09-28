
CHAIN   |   P2P   | RPC |   GRPC    |   API |   NODE    |   PEERS   
--------|---------|-----|-----------|-------|-----------|-----------
gaia|2010|2011|2012|2013|2011|bf8328b66dceb4987e5cd94430af66045e59899f@public-seed.cosmos.vitwit.com:26656<br />cfd785a4224c7940e9a10f6c1ab24c343e923bec@164.68.107.188:26656<br />d72b3011ed46d783e369fdf8ae2055b99a1e5074@173.249.50.25:26656<br />ba3bacc714817218562f743178228f23678b2873@public-seed-node.cosmoshub.certus.one:26656<br />3c7cad4154967a294b3ba1cc752e40e8779640ad@84.201.128.115:26656<br />366ac852255c3ac8de17e11ae9ec814b8c68bddb@51.15.94.196:26656
regen|2060|2061|2062|2063|2061|
akash|2020|2021|2022|2023|2021|
*juno|2070|2071|2072|2073|2071|
*sifnode|2110|2111|2112|2113|2111|
*anon|2100|2101|2102|2103|2101|
*starname|2050|2051|2052|2053|2051|
*chain-main|2040|2041|2042|2043|2041|
*omniflixhub|2120|2121|2122|2123|2121|
*dig|2090|2091|2092|2093|2091|stopped
*persistencecore|2080|2081|2082|2083|2081|
*osmosis|2000|2001|2002|2003|2001|
*umee|2030|2031|2032|2033|2031|a9a84866786013f75138388fbf12cdfc425bd39c@137.184.69.184:26656<br />684dd9ce7746041d0453322808cc5b238861e386@137.184.65.210:26656<br /> c4c425c66d2941ce4d5d98185aa90d2330de5efd@143.244.166.155:26656<br /> eb42bdbd821fad7bd0048a741237625b4d954d18@143.244.165.138:26656
*ixo|2130|2131|2132|2133|2131|not found
sentinel|2140|2141|2142|2143|2141|152bad169bfde238d24b8e2403d72c092adc107b@54.169.185.248:26656<br />57dbef4a8637f4c14dc5f8a4070ff07cc3de8380@13.212.44.171:26656<br />cb9a308bd21b745ecd58236a08bc60046b06fec3@13.233.250.145:26656<br />a77f6a094578dad899e2f40e0626b4c6d4705311@3.36.165.232:26656<br />5f7164bbf0e74bc0b7bc624c631b559bde6d52b4@165.22.65.48:26656<br />647e54e22cfcdf97b42ada11fcef2f0b5bd81230@35.163.249.152:31358<br />387027e3b1180d3a619cbbf3462704a490785963@54.176.90.228:26656
*irisnet|2150|2151|2152|2153|2151|fdc0406afdd3acc63f74f5439e09104f663a7c1f@44.241.177.178:26656<br />090bcbe5302e6104821a96c4899912870db04cb9@52.11.128.123:26656<br />83b3f989f3ce089afdf733f8aa06e792d7e00c08@3.34.6.30:26656<br />87f18756b93d835c59fe5ce2a8da51858837eb5b@54.180.15.28:26656<br />90e48220190b16cad95145b6213d512d703e5617@138.197.158.189:26656<br />7fad2da10c41b0c1e3c2ce6e708f7fa817b5e19d@135.181.56.26:46656<br />ebfb43ca1b592b5f8a1faf3e2aa1a34e8e1099cc@iris01.dokia.cloud:26656<br />a17d7923293203c64ba75723db4d5f28e642f469@seed-2.mainnet.irisnet.org:26656<br />fbaf634a899c7aab3c159ce1a345122bbeca3717@209.133.200.154:26656<br />92fadc989ed29aee0d46afce3226f8565d1f36cb@144.91.116.17:46656<br />895d5a5009d042108783a6aeb0991c5186a46617@144.76.96.47:26656<br />40821d0ade83d582b29d748f37ecf7bef0a823d0@66.42.116.195:26656<br />f4af63df2f5c63428be776e56ffc2899fa47afdf@47.101.160.78:26656<br />08e2f9453541b104df84efa68ab2f0d242eb829b@176.9.47.69:26656<br />db3dacf404840e067b2f59e304cb2b6662ec0cea@173.212.212.252:26656<br />87525da8c830da2c3a861638a77f601278efd353@185.181.103.142:26656<br />4ac6200974d3fd80a8e49d145a2c254ed37a9b9a@159.69.106.156:26656<br />4e02a4b4f4350ea2b770cd03dc41fedcadb13176@159.69.55.206:26656<br />5d659b3edde90344489210f5be90c0682b54b997@49.232.82.149:26656<br />63f5646b5f9ce927241383a091b60f797796588f@143.110.240.198:26656<br />84cc32adca3986b35953886ad075431d318a98b5@52.214.130.28:46656
*kusama|2160|2161|2162|2163|2161|not found
---


# Gaia
```bash
git clone https://github.com/cosmos/gaia.git
cd gaia
make install
gaiad init notional
wget https://github.com/cosmos/mainnet/raw/master/genesis.cosmoshub-4.json.gz
gzip -d genesis.cosmoshub-4.json.gz
mv genesis.cosmoshub-4.json ~/.gaia/config/genesis.json
nano ~/.gaia/config/app.toml # Change the minimum gas price to 2.025uatom
nano /etc/systemd/system/gaia.service # Make a systemd file with variables from above table
systemctl daemon-reload
systemctl enable gaia
systemctl start gaia

```
Till now, there still aren't any errors when starting `gaia`.

# Umee
```bash
git clone https://github.com/umee-network/umee.git
cd umee
make install
umeed init notional
wget -O ~/.umee/config/genesis.json https://raw.githubusercontent.com/umee-network/umee/main/networks/umee-betanet-2/genesis.json
nano /etc/systemd/system/umee.service # Make a systemd file with variables from above table
systemctl daemon-reload
systemctl enable umee
systemctl start umee
```
There is a problem with umee. It can't catch block `ADC5236719318B7E2EE971D14F3302681886A587D395BA83240D15707A2D1696` with this error:
```
panic: Failed to process committed block (2:BF8B7BE0F53486464F40EF58C2704467A8371FC64F5DDA45D46DFBE8230838B8): wrong Block.Header.AppHash.  Expected ADC5236719318B7E2EE971D14F3302681886A587D395BA83240D15707A2D1696<br /> got 65AF964E1763F7259F76C46BFD031E7EB2A3314AE6629662252B61BE762264DE
```
It is often caused by the outdated version of umee. But in this case, umee is setted up to the newest version.

# Regen, Akash
As in the web

# Sentinel
```bash
git clone https://github.com/sentinel-official/hub.git
cd hub
git checkout v0.7.0
make install
sentinelhub init notional --chain-id sentinelhub-2
wget https://github.com/sentinel-official/networks/raw/main/sentinelhub-2/genesis.zip
unzip genesis.zip -d ~/.sentinelhub/config/
nano /etc/systemd/system/sentinel.service # Make a systemd file with variables from above table
systemctl daemon-reload
systemctl enable sentinel
systemctl start sentinel
```
Till now, there still aren't any errors when starting `gaia`.

# Irisnet
```bash
git clone https://github.com/irisnet/irishub.git
cd irishub
make install 
iris init notional --chain-id=irishub-1
curl -o ~/.iris/config/config.toml https://raw.githubusercontent.com/irisnet/mainnet/master/config/config.toml
curl -o ~/.iris/config/genesis.json https://raw.githubusercontent.com/irisnet/mainnet/master/config/genesis.json
nano /etc/systemd/system/iris.service # Make a systemd file with variables from above table
systemctl daemon-reload
systemctl enable iris
systemctl start iris
```
There is a problem with iris:
```
panic: unknown field "pending_htlcs" in types.GenesisState
```

# 