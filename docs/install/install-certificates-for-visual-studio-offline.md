---
title: Instalace certifikátů požadovaných pro offline instalaci
description: Přečtěte si, jak nainstalovat certifikáty pro offline instalaci sady Visual Studio.
ms.date: 08/08/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9750A3F3-89C7-4A8F-BA75-B0B06BD772C2
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: b2570876ddaa03753b1c0d3fb9f9ddc772bbbcb8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114663"
---
# <a name="install-certificates-required-for-visual-studio-offline-installation"></a>Instalace certifikátů požadovaných pro offline instalaci sady Visual Studio

Visual Studio je primárně určen k instalaci na počítači připojeném k internetu, protože mnoho součástí jsou pravidelně aktualizovány. S některými dalšími kroky je však možné nasadit Visual Studio v prostředí, kde není k dispozici funkční připojení k internetu.

Modul nastavení sady Visual Studio nainstaluje pouze obsah, který je důvěryhodný. Je to tím, že kontroluje Authenticode podpisy obsahu, který je stažen a ověření, že veškerý obsah je důvěryhodný před instalací. Tím je vaše prostředí v bezpečí před útoky, kde je ohroženo umístění pro stahování. Nastavení sady Visual Studio proto vyžaduje, aby bylo v počítači uživatele nainstalováno a aktuální několik standardních kořenových a zprostředkujících certifikátů microsoftu. Pokud byl počítač udržován v aktuálním stavu pomocí služby Windows Update, podpisové certifikáty jsou obvykle aktuální. Pokud je zařízení připojeno k Internetu, může visual studio během instalace aktualizovat certifikáty podle potřeby k ověření podpisů souborů. Pokud je počítač offline, certifikáty musí být aktualizovány jiným způsobem.

## <a name="how-to-refresh-certificates-when-offline"></a>Jak aktualizovat certifikáty v offline

Existují tři možnosti instalace nebo aktualizace certifikátů v prostředí offline.

### <a name="option-1---manually-install-certificates-from-a-layout-folder"></a>Možnost 1 – Ruční instalace certifikátů ze složky rozložení

::: moniker range="vs-2017"

Při vytváření rozložení sítě se potřebné certifikáty stáhnou do složky Certifikáty. Certifikáty pak můžete ručně nainstalovat poklepáním na jednotlivé soubory certifikátů a potom klepnutím na průvodce Správce množte. Pokud budete požádáni o zadání hesla, ponechte ho prázdné.

**Aktualizace**: Pro Visual Studio 2017 verze 15.8 Náhled 2 nebo novější můžete certifikáty nainstalovat ručně tak, že kliknete pravým tlačítkem myši na jednotlivé soubory certifikátu, vyberete instalační certifikát a potom kliknete na průvodce Správcem certifikátů.

::: moniker-end

::: moniker range="vs-2019"

Při vytváření rozložení sítě se potřebné certifikáty stáhnou do složky Certifikáty. Certifikáty můžete nainstalovat ručně tak, že kliknete pravým tlačítkem myši na jednotlivé soubory certifikátu, vyberete možnost Instalovat certifikát a potom kliknete na průvodce Správcem certifikátů. Pokud budete požádáni o zadání hesla, ponechte ho prázdné.

::: moniker-end

### <a name="option-2---distribute-trusted-root-certificates-in-an-enterprise-environment"></a>Možnost 2 – Distribuce důvěryhodných kořenových certifikátů v podnikovém prostředí

U podniků s offline počítači, které nemají nejnovější kořenové certifikáty, může správce k jejich aktualizaci použít pokyny na stránce [Konfigurovat důvěryhodné kořeny a Nepovolené certifikáty.](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265983(v=ws.11))

### <a name="option-3---install-certificates-as-part-of-a-scripted-deployment-of-visual-studio"></a>Možnost 3 – Instalace certifikátů jako součást skriptovaného nasazení sady Visual Studio

Pokud skriptujete nasazení sady Visual Studio v offline prostředí pro klientské pracovní stanice, postupujte takto:

::: moniker range="vs-2017"

1. Zkopírujte [nástroj Správce certifikátů](/dotnet/framework/tools/certmgr-exe-certificate-manager-tool) (certmgr.exe) do \\sdílené složky instalace (například server\share\vs2017). Certmgr.exe není součástí samotného systému Windows, ale je k dispozici jako součást [sady Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

2. Vytvořte dávkový soubor s následujícími příkazy:

   ```cmd
   certmgr.exe -add -c certificates\manifestSignCertificates.p12 -n "Microsoft Code Signing PCA 2011" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\manifestSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

   certmgr.exe -add -c certificates\manifestCounterSignCertificates.p12 -n "Microsoft Time-Stamp PCA 2010" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\manifestCounterSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

   certmgr.exe -add -c certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   ```

   **Aktualizace**: Pro Visual Studio 2017 verze 15.8 Náhled 2 nebo novější vytvořte dávkový soubor s následujícími příkazy:

   ```cmd
   certmgr.exe -add [layout path]\certificates\manifestRootCertificate.cer -n "Microsoft Root Certificate Authority 2011" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\manifestCounterSignRootCertificate.cer -n "Microsoft Root Certificate Authority 2010" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\vs_installer_opc.RootCertificate.cer -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   ```
   
   Případně vytvořte dávkový soubor, který používá certutil.exe, který je dodáván se systémem Windows, s následujícími příkazy:
   
      ```cmd
   certutil.exe -addstore -f "Root" "[layout path]\certificates\manifestRootCertificate.cer"

   certutil.exe -addstore -f "Root" "[layout path]\certificates\manifestCounterSignRootCertificate.cer"

   certutil.exe -addstore -f "Root" "[layout path]\certificates\vs_installer_opc.RootCertificate.cer"
   ```

3. Nasaďte dávkový soubor do klienta. Tento příkaz by měl být spuštěn z procesu se zvýšenými oprávněními.

::: moniker-end

::: moniker range="vs-2019"

1. Zkopírujte [nástroj Správce certifikátů](/dotnet/framework/tools/certmgr-exe-certificate-manager-tool) (certmgr.exe) do \\sdílené složky instalace (například server\share\vs2019). Certmgr.exe není součástí samotného systému Windows, ale je k dispozici jako součást [sady Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

2. Vytvořte dávkový soubor s následujícími příkazy:

   ```cmd
   certmgr.exe -add [layout path]\certificates\manifestRootCertificate.cer -n "Microsoft Root Certificate Authority 2011" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\manifestCounterSignRootCertificate.cer -n "Microsoft Root Certificate Authority 2010" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\vs_installer_opc.RootCertificate.cer -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   ```
   
   Případně vytvořte dávkový soubor, který používá certutil.exe, který je dodáván se systémem Windows, s následujícími příkazy:
   
      ```cmd
   certutil.exe -addstore -f "Root" "[layout path]\certificates\manifestRootCertificate.cer

   certutil.exe -addstore -f "Root" [layout path]\certificates\manifestCounterSignRootCertificate.cer"

   certutil.exe -addstore -f "Root" "[layout path]\certificates\vs_installer_opc.RootCertificate.cer"
   ```

3. Nasaďte dávkový soubor do klienta. Tento příkaz by měl být spuštěn z procesu se zvýšenými oprávněními.

::: moniker-end

## <a name="what-are-the-certificates-files-in-the-certificates-folder"></a>Jaké jsou soubory certifikátů ve složce Certifikáty?

::: moniker range="vs-2017"

Tři . Soubory P12 v této složce obsahují zprostředkující certifikát a kořenový certifikát. Většina systémů, které jsou aktuální se službou Windows Update, má tyto certifikáty již nainstalovány.

* **ManifestSignCertificates.p12** obsahuje:
  * Zprostředkující certifikát: **Microsoft Code Signing PCA 2011**
    * Není vyžadováno. Zlepšuje výkon v některých scénářích, pokud je k dispozici.
  * Kořenový certifikát: **Microsoft Root Certificate Authority 2011**
    * Povinné v systémech Windows 7 Service Pack 1, které nemají nainstalovány nejnovější aktualizace systému Windows.
* **ManifestCounterSignCertificates.p12** obsahuje:
  * Zprostředkující certifikát: **Microsoft Time-Stamp PCA 2010**
    * Není vyžadováno. Zlepšuje výkon v některých scénářích, pokud je k dispozici.
  * Kořenový certifikát: **Microsoft Root Certificate Authority 2010**
    * Vyžadováno pro systémy Windows 7 Service Pack 1, které nemají nainstalovány nejnovější aktualizace systému Windows.
* **Vs_installer_opc. SignCertificates.p12** obsahuje:
  * Zprostředkující certifikát: **Microsoft Code Signing PCA**
    * Vyžadováno pro všechny systémy. Všimněte si, že systémy se všemi aktualizacemi použitými ze služby Windows Update nemusí mít tento certifikát.
  * Kořenový certifikát: **Kořenová certifikační autorita společnosti Microsoft**
    * Povinná hodnota. Tento certifikát je dodáván se systémy se systémem Windows 7 nebo novějším.

**Aktualizace**: Pro Visual Studio 2017 verze 15.8 Náhled 2 nebo novější, Instalační služba Sady Visual Studio vyžaduje pouze kořenové certifikáty, které mají být nainstalovány v systému. Tyto certifikáty jsou uloženy v souborech CER namísto .p12.

::: moniker-end

::: moniker range="vs-2019"

* **ManifestSignCertificates.cer** obsahuje:
  * Kořenový certifikát: **Microsoft Root Certificate Authority 2011**
    * Povinné v systémech Windows 7 Service Pack 1, které nemají nainstalovány nejnovější aktualizace systému Windows.
* **Soubor ManifestCounterSignCertificates.cer** obsahuje:
  * Kořenový certifikát: **Microsoft Root Certificate Authority 2010**
    * Vyžadováno pro systémy Windows 7 Service Pack 1, které nemají nainstalovány nejnovější aktualizace systému Windows.
* **Vs_installer_opc. SignCertificates.cer** obsahuje:
  * Kořenový certifikát: **Kořenová certifikační autorita společnosti Microsoft**
    * Povinná hodnota. Tento certifikát je dodáván se systémy se systémem Windows 7 nebo novějším.

Instalační služba sady Visual Studio vyžaduje, aby byly v systému nainstalovány pouze kořenové certifikáty.

::: moniker-end

## <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>Proč nejsou certifikáty ze složky Certifikáty nainstalovány automaticky?

Při ověření podpisu v online prostředí se rozhraní API systému Windows používají ke stažení a přidání certifikátů do systému. Během tohoto procesu dojde k ověření, že certifikát je důvěryhodný a povolený prostřednictvím nastavení správy. Tento proces ověření nemůže proběhnout ve většině offline prostředí. Ruční instalace certifikátů umožňuje správcům rozlehlé sítě zajistit, aby byly certifikáty důvěryhodné a splňovaly zásady zabezpečení jejich organizace.

## <a name="checking-if-certificates-are-already-installed"></a>Kontrola, zda jsou certifikáty již nainstalovány

Jedním ze způsobů, jak zkontrolovat instalační systém, je následující kroky:

1. Spusťte **soubor mmc.exe**.<br/>
  a. Klepněte na **soubor**a pak vyberte **Přidat nebo odebrat modul snap-in**.<br/>
  b. Poklepejte na **certifikáty**, vyberte **účet počítače**a potom klepněte na tlačítko **Další**.<br/>
  c. Vyberte **Místní počítač**, klepněte na tlačítko **Dokončit**a potom klepněte na tlačítko **OK**.<br/>
  d. Rozbalte **certifikáty (místní počítač).**<br/>
  e. Rozbalte **důvěryhodné kořenové certifikační úřady**a vyberte **certifikáty**.<br/>
    * Zkontrolujte, zda v tomto seznamu najdete potřebné kořenové certifikáty.<br/>

   f. Rozbalte **zprostředkující certifikační úřady**a vyberte **certifikáty**.<br/>
    * V tomto seznamu naleznete požadované zprostředkující certifikáty.<br/>

2. Klepněte na **soubor**a pak vyberte **Přidat nebo odebrat modul snap-in**.<br/>
  a. Poklepejte na **položku Certifikáty**, vyberte **můj uživatelský účet**, klepněte na tlačítko **Dokončit**a potom klepněte na tlačítko **OK**.<br/>
  b. Rozbalte **certifikáty – aktuální uživatel**.<br/>
  c. Rozbalte **zprostředkující certifikační úřady**a vyberte **certifikáty**.<br/>
    * V tomto seznamu naleznete požadované zprostředkující certifikáty.<br/>

Pokud názvy certifikátů nebyly ve sloupcích **Vystaveno do,** musí být nainstalovány.  Pokud zprostředkující certifikát byl pouze v **úložišti aktuální zprostředkující** uživatel certifikát, pak je k dispozici pouze pro uživatele, který je přihlášen. Možná budete muset nainstalovat pro ostatní uživatele.

## <a name="install-visual-studio"></a>Instalace sady Visual Studio

Po instalaci certifikátů může nasazení sady Visual Studio pokračovat pomocí pokynů z části [Nasazení ze síťové instalace](create-a-network-installation-of-visual-studio.md#deploy-from-a-network-installation) na stránce Vytvoření síťové instalace sady Visual Studio.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Instalace sady Visual Studio](install-visual-studio.md)
* [Průvodce správcem sady Visual Studio](visual-studio-administrator-guide.md)
* [Instalace sady Visual Studio pomocí parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
* [ID úloh a komponent sady Visual Studio](workload-and-component-ids.md)
