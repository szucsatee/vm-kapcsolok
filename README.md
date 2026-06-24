# Azure CLI `az vm create` Cheat Sheet & Példák

Ez a repository az Azure CLI `az vm create` parancsának legfontosabb és leggyakrabban használt kapcsolóit gyűjti össze kategóriák szerint csoportosítva, gyors puskaként (cheat sheet) és indítószkriptként.

## Tartalomjegyzék
- [Gyors elérés parancssorból](#gyors-elérés-parancssorból)
- [Kategóriák és Kapcsolók](#kategóriák-és-kapcsolók)
- [Használati példa](#használati-példa)

## Gyors elérés parancssorból
Az összes elérhető kapcsoló és a teljes, aktuális angol leírás lekérése:
```cmd
az vm create --help
```
  
---

## Kategóriák és Kapcsolók

### 1. Kötelező és Alapvető kapcsolók
- `-g`, `--resource-group` : Az erőforráscsoport neve, ahová a VM kerülni fog.
- `-n`, `--name` : A virtuális gép neve.
- `--image` : Az operációs rendszer lemezképe (pl. `Ubuntu2204`, `Win2022Datacenter`, vagy egyedi URI).
- `--location` / `-l` : Az Azure régió (pl. `westeurope`, `eastus`).

### 2. Hitelesítés és Hozzáférés
- `--admin-username` : A VM adminisztrátor felhasználóneve.
- `--admin-password` : A VM jelszava (Windows esetén kötelező, Linuxnál választható).
- `--ssh-key-values` : Az SSH nyilvános kulcs(ok) elérési útja vagy szöveges értéke (Linuxhoz).
- `--generate-ssh-keys` : Automatikusan generál SSH kulcspárt, ha nem létezik.

### 3. Hardver és Teljesítmény
- `--size` : A virtuális gép mérete / típusa (pl. `Standard_D2s_v5`, `Standard_B2s`). Alapértelmezett: `Standard_DS1_v2`.
- `--edge-zone` : Az Edge zóna azonosítója, ha nem alapértelmezett régióba építesz.

### 4. Hálózati beállítások (Networking)
- `--vnet-name` : A virtuális hálózat (VNet) neve.
- `--subnet` : Az alhálózat (Subnet) neve.
- `--public-ip-address` : Nyilvános IP-cím neve, vagy `""` (üres), ha nem kérsz nyilvános IP-t.
- `--public-ip-sku` : A nyilvános IP típusa (`Basic` vagy `Standard`).
- `--nsg` : A hálózati biztonsági csoport (NSG) neve.
- `--nsg-rule` : Biztonsági szabály típusa (pl. `RDP` Windows-hoz vagy `SSH` Linux-hoz).
- `--open-ports` : Konkrét portok megnyitása a külvilág felé (pl. `22 80 443`).

### 5. Tárhely és Lemezek (Storage & Disks)
- `--os-disk-name` : Az operációs rendszer lemezének neve.
- `--os-disk-size-gb` : Az OS lemez mérete gigabájtban.
- `--os-disk-type` : A lemez teljesítménye (pl. `Standard_LRS`, `Premium_LRS`, `StandardSSD_LRS`).
- `--data-disks` : További adatlemezek hozzáadása méret vagy meglévő lemez alapján.
- `--attach-data-disks` : Már meglévő menedzselt lemezek csatolása.

### 6. Rendelkezésre állás és Biztonság (Availability & Security)
- `--availability-set` : Rendelkezésre állási csoport neve.
- `--zone` / `-z` : Konkrét elérhetőségi zóna kiválasztása (pl. `1`, `2` vagy `3`).
- `--security-type` : Biztonsági szint (pl. `TrustedLaunch` vagy `Standard`).
- `--enable-vtpm` : Virtuális TPM modul engedélyezése (Trusted Launch-hoz).

### 7. Felügyelet és Automatizáció
- `--tags` : Címkék hozzáadása kulcs=érték formában (pl. `Environment=Dev Project=Alpha`).
- `--custom-data` : Inicializáló szkript (cloud-init) megadása, ami a VM első indulásakor fut le.
- `--assign-identity` : Managed Identity hozzárendelése (pl. `[system]` a rendszer által felügyelt identitáshoz).
