---
title: 'Postup: Konfigurace chování výzvy důvěryhodnosti clickonce | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- deploying applications [ClickOnce], trust prompt
- ClickOnce applications, install without prompting
- ClickOnce applications, trust prompt
- ClickOnce deployment, trust prompt
ms.assetid: cc04fa75-012b-47c9-9347-f4216be23cf2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ec5f1cca49f1b799b39969849e0a73bf1e6e296d
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649149"
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>Postup: Konfigurace chování výzvy k důvěře ClickOnce
Výzvu důvěryhodnosti ClickOnce můžete nakonfigurovat tak, aby bylo možné určit, zda budou koncoví uživatelé mít možnost instalovat aplikace ClickOnce, jako jsou aplikace Windows Forms, aplikace Služby Předpopočítače, konzolové aplikace, aplikace prohlížeče WPF a řešení sady Office. Výzvu důvěryhodnosti nakonfigurujete nastavením klíčů registru v počítači každého koncového uživatele.

 V následující tabulce jsou uvedeny možnosti konfigurace, které lze použít pro každou z pěti zón (Internet, Nedůvěryhodné weby, MyComputer, LocalIntranet a TrustedSites).

|Možnost|Hodnota nastavení registru|Popis|
|------------|----------------------------|-----------------|
|Povolte výzvu důvěryhodnosti.|`Enabled`|Zobrazí se výzva důvěryhodnosti ClickOnce, aby koncoví uživatelé mohli aplikacím ClickOnce udělit důvěryhodnost.|
|Omezte výzvu důvěryhodnosti.|`AuthenticodeRequired`|Výzva důvěryhodnosti ClickOnce se zobrazí pouze v případě, že jsou aplikace ClickOnce podepsány certifikátem, který identifikuje vydavatele.|
|Zakažte výzvu důvěryhodnosti.|`Disabled`|Výzva důvěryhodnosti ClickOnce se nezobrazí pro všechny aplikace ClickOnce, které nejsou podepsány explicitně důvěryhodným certifikátem.|

 V následující tabulce je uvedeno výchozí chování pro každou zónu. Sloupec Aplikace odkazuje na aplikace windows forms, aplikace Nadace pro prezentaci systému Windows, aplikace prohlížeče WPF a konzolové aplikace.

|Zóna|Aplikace|řešení Office|
|----------|------------------|----------------------|
|`MyComputer`|`Enabled`|`Enabled`|
|`LocalIntranet`|`Enabled`|`Enabled`|
|`TrustedSites`|`Enabled`|`Enabled`|
|`Internet`|`Enabled`|`AuthenticodeRequired`|
|`UntrustedSites`|`Disabled`|`Disabled`|

 Tato nastavení můžete přepsat povolením, omezením nebo zakázáním výzvy důvěryhodnosti ClickOnce.

## <a name="enable-the-clickonce-trust-prompt"></a>Povolení výzvy důvěryhodnosti ClickOnce
 Povolte výzvu důvěryhodnosti pro zónu, pokud chcete, aby se koncovým uživatelům nabídla možnost instalace a spuštění libovolné aplikace ClickOnce, která pochází z této zóny.

#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Povolení výzvy důvěryhodnosti ClickOnce pomocí editoru registru

1. Otevřete editor registru: .

    1. Klepněte na tlačítko **Start**a potom klepněte na tlačítko **Spustit**.

    2. Do pole **Otevřít** `regedit`zadejte a klepněte na tlačítko **OK**.

2. Vyhledejte následující klíč registru:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**

     Pokud klíč neexistuje, vytvořte jej.

3. Přidejte následující podklíče jako **řetězcová hodnota**, pokud ještě neexistují, s přidruženými hodnotami uvedenými v následující tabulce.

    |Podklíč Hodnota řetězce|Hodnota|
    |-------------------------|-----------|
    |`Internet`|`Enabled`|
    |`UntrustedSites`|`Disabled`|
    |`MyComputer`|`Enabled`|
    |`LocalIntranet`|`Enabled`|
    |`TrustedSites`|`Enabled`|

     Pro řešení `Internet` sady Office `AuthenticodeRequired` má `UntrustedSites` výchozí `Disabled`hodnotu a má hodnotu . Pro všechny `Internet` ostatní má `Enabled`výchozí hodnotu .

#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>Povolení výzvy důvěryhodnosti ClickOnce programově

1. Vytvořte konzolovou aplikaci visual basicu nebo jazyka Visual C# v sadě Visual Studio.

2. Otevřete soubor *Program.vb* nebo *Program.cs* pro úpravy a přidejte následující kód.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "Enabled")
    key.SetValue("LocalIntranet", "Enabled")
    key.SetValue("Internet", "Enabled")
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

## <a name="restrict-the-clickonce-trust-prompt"></a>Omezit výzvu důvěryhodnosti ClickOnce
 Omezte výzvu důvěryhodnosti, aby řešení musela být podepsána certifikáty Authenticode, které byly známy identitu před tím, než budou uživatelé vyzváni k rozhodnutí o důvěryhodnosti.

#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Omezení výzvy důvěryhodnosti ClickOnce pomocí editoru registru

1. Otevřete editor registru: .

    1. Klepněte na tlačítko **Start**a potom klepněte na tlačítko **Spustit**.

    2. Do pole **Otevřít** `regedit`zadejte a klepněte na tlačítko **OK**.

2. Vyhledejte následující klíč registru:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**

     Pokud klíč neexistuje, vytvořte jej.

3. Přidejte následující podklíče jako **řetězcová hodnota**, pokud ještě neexistují, s přidruženými hodnotami uvedenými v následující tabulce.

    |Podklíč Hodnota řetězce|Hodnota|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`AuthenticodeRequired`|
    |`MyComputer`|`AuthenticodeRequired`|
    |`LocalIntranet`|`AuthenticodeRequired`|
    |`TrustedSites`|`AuthenticodeRequired`|

#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>Chcete-li příkaz ClickOnce programově omezit výzvu důvěryhodnosti ClickOnce

1. Vytvořte konzolovou aplikaci visual basicu nebo jazyka Visual C# v sadě Visual Studio.

2. Otevřete soubor *Program.vb* nebo *Program.cs* pro úpravy a přidejte následující kód.

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

## <a name="disable-the-clickonce-trust-prompt"></a>Zakázání výzvy k důvěryhodnosti clickonce
 Výzvu důvěryhodnosti můžete zakázat, aby koncoví uživatelé neměli možnost instalovat řešení, která ještě nejsou v zásadách zabezpečení důvěryhodná.

#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Zakázání výzvy důvěryhodnosti ClickOnce pomocí editoru registru

1. Otevřete editor registru: .

    1. Klepněte na tlačítko **Start**a potom klepněte na tlačítko **Spustit**.

    2. Do pole **Otevřít** `regedit`zadejte a klepněte na tlačítko **OK**.

2. Vyhledejte následující klíč registru:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**

     Pokud klíč neexistuje, vytvořte jej.

3. Přidejte následující podklíče jako **řetězcová hodnota**, pokud ještě neexistují, s přidruženými hodnotami uvedenými v následující tabulce.

    |Podklíč Hodnota řetězce|Hodnota|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`Disabled`|
    |`MyComputer`|`Disabled`|
    |`LocalIntranet`|`Disabled`|
    |`TrustedSites`|`Disabled`|

#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>Chcete-li příkaz ClickOnce zakázat výzvu důvěryhodnosti programově

1. Vytvořte konzolovou aplikaci visual basicu nebo jazyka Visual C# v sadě Visual Studio.

2. Otevřete soubor *Program.vb* nebo *Program.cs* pro úpravy a přidejte následující kód.

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
- [Zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md)
- [Zabezpečení přístupu ke kódu pro aplikace ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce a kód Authenticode](../deployment/clickonce-and-authenticode.md)
- [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md)
- [Postup: Povolení nastavení zabezpečení ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)
- [Postup: Nastavení zóny zabezpečení pro aplikaci ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Postup: Nastavení vlastních oprávnění pro aplikaci ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Postup: Ladění aplikace ClickOnce s omezenými oprávněními](securing-clickonce-applications.md)
- [Postup: Přidání důvěryhodného vydavatele do klientského počítače pro aplikace ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Postup: Opětovné podepsání manifestů aplikací a nasazení](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
