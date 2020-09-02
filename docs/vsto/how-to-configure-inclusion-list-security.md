---
title: 'Postupy: Konfigurace zabezpečení seznamu zahrnutí'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio
- inclusion lists [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 459cf3f33197939a916a5f11a94bbaf09e8142e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85541632"
---
# <a name="how-to-configure-inclusion-list-security"></a>Postupy: Konfigurace zabezpečení seznamu zahrnutí
  Pokud máte oprávnění správce, můžete nakonfigurovat [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] výzvu vztahu důvěryhodnosti, abyste mohli řídit, jestli mají koncoví uživatelé možnost instalovat řešení Office, a to uložením rozhodnutí o důvěryhodnosti do seznamu povolených. Informace o seznamech zahrnutí najdete v tématu [důvěryhodná řešení Office pomocí seznamů zahrnutí](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Pro řešení, která jsou v každé z pěti zón, můžete nastavit následující možnosti:

- Povolte [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] klíč výzvy vztahu důvěryhodnosti a seznam zahrnutí. Koncovým uživatelům můžete umožnit udělit vztah důvěryhodnosti k řešením Office, která jsou podepsaná jakýmkoli certifikátem.

- Omezte [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] klíč výzvy vztahu důvěryhodnosti a seznam zahrnutí. Koncovým uživatelům můžete dovolit instalovat řešení Office, která jsou podepsaná certifikátem, který identifikuje vydavatele, ale ještě není důvěryhodný.

- Zakažte [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] klíč výzvy vztahu důvěryhodnosti a seznam zahrnutí. Koncovým uživatelům můžete zabránit v instalaci jakéhokoli řešení Office, které není podepsané explicitně důvěryhodným certifikátem.

## <a name="enable-the-inclusion-list"></a>Povolit seznam zahrnutí
 Seznam zahrnutí pro zónu povolte, pokud chcete koncovým uživatelům prezentovat možnost instalace a spuštění libovolného řešení Office, které pochází z této zóny.

### <a name="to-enable-the-inclusion-list-by-using-the-registry-editor"></a>Povolení seznamu zahrnutí pomocí Editoru registru

1. Otevřete editor registru: .

    1. Klikněte na tlačítko **Start**a potom na příkaz **Spustit**.

    2. Do pole **otevřít** zadejte **regedt32.exe**a pak klikněte na **OK**.

2. Vyhledejte následující klíč registru:

     **\ HKEY_LOCAL_MACHINE \SOFTWARE\MICROSOFT \\ . NETFramework\Security\TrustManager\PromptingLevel**

     Pokud klíč neexistuje, vytvořte ho.

3. Přidejte následující podklíče jako **řetězcovou hodnotu**, pokud ještě neexistují, s přidruženými hodnotami.

    |Řetězcová hodnota – podklíč|Hodnota|
    |-------------------------|-----------|
    |**Internet**|**AuthenticodeRequired**|
    |**UntrustedSites**|**Zakázáno**|
    |**MyComputer**|**Povoleno**|
    |**LocalIntranet**|**Povoleno**|
    |**TrustedSites**|**Povoleno**|

     Ve výchozím nastavení má **Internet** hodnotu **AuthenticodeRequired** a **UntrustedSites** má hodnotu **disabled**.

### <a name="to-enable-the-inclusion-list-programmatically"></a>Povolení seznamu povolených programů prostřednictvím kódu programu

1. Vytvořte Visual Basic nebo konzolovou aplikaci Visual C#.

2. Otevřete soubor *program. vb* nebo *program.cs* pro úpravy a přidejte následující kód.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "Enabled")
    key.SetValue("LocalIntranet", "Enabled")
    key.SetValue("Internet", "AuthenticodeRequired")
    key.SetValue("TrustedSites", "Enabled")
    key.SetValue("UntrustedSites", "Disabled")
    key.Close()
    ```

    ```csharp
    Microsoft.Win32.RegistryKey key;
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");
    key.SetValue("MyComputer", "Enabled");
    key.SetValue("LocalIntranet", "Enabled");
    key.SetValue("Internet", "AuthenticodeRequired");
    key.SetValue("TrustedSites", "Enabled");
    key.SetValue("UntrustedSites", "Disabled");
    key.Close();
    ```

3. Sestavte a spusťte aplikaci.

## <a name="restrict-the-inclusion-list"></a>Omezit seznam zahrnutí
 Omezte seznam zahrnutí, aby řešení musela být podepsaná certifikáty Authenticode, které mají známou identitu před tím, než se uživatelům zobrazí výzva k rozhodnutí o důvěryhodnosti.

### <a name="to-restrict-the-inclusion-list"></a>Omezení seznamu zahrnutí

1. Otevřete editor registru: .

    1. Klikněte na tlačítko **Start**a potom na příkaz **Spustit**.

    2. Do pole **otevřít** zadejte **regedt32.exe**a pak klikněte na **OK**.

2. Vyhledejte následující klíč registru:

     **\ HKEY_LOCAL_MACHINE \SOFTWARE\MICROSOFT \\ . NETFramework\Security\TrustManager\PromptingLevel**

     Pokud klíč neexistuje, vytvořte ho.

3. Přidejte následující podklíče jako **řetězcovou hodnotu**, pokud ještě neexistují, s přidruženými hodnotami.

    |Řetězcová hodnota – podklíč|Hodnota|
    |-------------------------|-----------|
    |**UntrustedSites**|**Zakázáno**|
    |**Internet**|**AuthenticodeRequired**|
    |**MyComputer**|**AuthenticodeRequired**|
    |**LocalIntranet**|**AuthenticodeRequired**|
    |**TrustedSites**|**AuthenticodeRequired**|

     Ve výchozím nastavení má **Internet** hodnotu **AuthenticodeRequired** a **UntrustedSites** má hodnotu **disabled**.

### <a name="to-restrict-the-inclusion-list-programmatically"></a>Chcete-li omezit seznam zahrnutí programově

1. Vytvořte Visual Basic nebo konzolovou aplikaci Visual C#.

2. Otevřete soubor *program. vb* nebo *program.cs* pro úpravy a přidejte následující kód.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "AuthenticodeRequired")
    key.SetValue("LocalIntranet", "AuthenticodeRequired")
    key.SetValue("Internet", "AuthenticodeRequired")
    key.SetValue("TrustedSites", "AuthenticodeRequired")
    key.SetValue("UntrustedSites", "Disabled")
    key.Close()
    ```

    ```csharp
    Microsoft.Win32.RegistryKey key;
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");
    key.SetValue("MyComputer", "AuthenticodeRequired");
    key.SetValue("LocalIntranet", "AuthenticodeRequired");
    key.SetValue("Internet", "AuthenticodeRequired");
    key.SetValue("TrustedSites", "AuthenticodeRequired");
    key.SetValue("UntrustedSites", "Disabled");
    key.Close();
    ```

3. Sestavte a spusťte aplikaci.

## <a name="disable-the-inclusion-list"></a>Zakázat seznam zahrnutí
 Seznam pro zahrnutí můžete zakázat, aby koncoví uživatelé mohli instalovat jenom řešení, která jsou podepsaná důvěryhodným a známým certifikátem.

### <a name="to-disable-the-inclusion-list"></a>Zakázání seznamu pro zahrnutí

1. Otevřete editor registru: .

    1. Klikněte na tlačítko **Start**a potom na příkaz **Spustit**.

    2. Do pole **otevřít** zadejte **regedt32.exe**a pak klikněte na **OK**.

2. Pokud tato akce ještě neexistuje, vytvořte následující klíč registru:

     **\ HKEY_LOCAL_MACHINE \SOFTWARE\MICROSOFT \\ . NETFramework\Security\TrustManager\PromptingLevel**

3. Přidejte následující podklíče jako **řetězcovou hodnotu**, pokud ještě neexistují, s přidruženými hodnotami.

    |Řetězcová hodnota – podklíč|Hodnota|
    |-------------------------|-----------|
    |**UntrustedSites**|**Zakázáno**|
    |**Internet**|**Zakázáno**|
    |**MyComputer**|**Zakázáno**|
    |**LocalIntranet**|**Zakázáno**|
    |**TrustedSites**|**Zakázáno**|

### <a name="to-disable-the-inclusion-list-programmatically"></a>Postup při zakazování seznamu povolených zahrnutí

1. Vytvořte Visual Basic nebo konzolovou aplikaci Visual C#.

2. Otevřete soubor *program. vb* nebo *program.cs* pro úpravy a přidejte následující kód.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "Disabled")
    key.SetValue("LocalIntranet", "Disabled")
    key.SetValue("Internet", "Disabled")
    key.SetValue("TrustedSites", "Disabled")
    key.SetValue("UntrustedSites", "Disabled")
    key.Close()
    ```

    ```csharp
    Microsoft.Win32.RegistryKey key;
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");
    key.SetValue("MyComputer", "Disabled");
    key.SetValue("LocalIntranet", "Disabled");
    key.SetValue("Internet", "Disabled");
    key.SetValue("TrustedSites", "Disabled");
    key.SetValue("UntrustedSites", "Disabled");
    key.Close();

    ```

3. Sestavte a spusťte aplikaci.

## <a name="see-also"></a>Viz také
- [Důvěryhodná řešení pro Office pomocí seznamů zahrnutí](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)
- [Zabezpečení řešení pro systém Office](../vsto/securing-office-solutions.md)
