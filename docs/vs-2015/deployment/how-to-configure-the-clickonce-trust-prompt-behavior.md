---
title: 'Postupy: Konfigurace chování výzvy důvěryhodnosti ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 58e5f0e9154137097a94637799966ee94818fca4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150832"
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>Postupy: Konfigurace chování výzvy důvěryhodnosti ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete nakonfigurovat výzvu vztahu důvěryhodnosti pro ClickOnce, která určuje, jestli mají koncoví uživatelé možnost instalovat aplikace ClickOnce, například model Windows Forms aplikace, Windows Presentation Foundation aplikace, konzolové aplikace, aplikace pro prohlížeč WPF a řešení pro Office. Výzvu pro důvěryhodnost konfigurujete nastavením klíčů registru pro jednotlivé počítače koncového uživatele.  
  
 V následující tabulce jsou uvedeny možnosti konfigurace, které lze použít pro každou z pěti zón (Internet, UntrustedSites, MyComputer, LocalIntranet a TrustedSites).  
  
|Možnost|Hodnota nastavení registru|Popis|  
|------------|----------------------------|-----------------|  
|Povolte dotaz Trust.|`Enabled`|Zobrazí se výzva vztahu důvěryhodnosti ClickOnce, aby koncoví uživatelé mohli udělovat důvěru aplikacím ClickOnce.|  
|Omezení výzvy vztahu důvěryhodnosti.|`AuthenticodeRequired`|Výzva k zobrazení výzvy důvěryhodnosti ClickOnce se zobrazí pouze v případě, že jsou aplikace ClickOnce podepsány certifikátem, který identifikuje vydavatele.|  
|Zakažte zobrazení výzvy vztahu důvěryhodnosti.|`Disabled`|Výzva k zobrazení výzvy důvěryhodnosti ClickOnce se nezobrazí pro žádné aplikace ClickOnce, které nejsou podepsané explicitně důvěryhodným certifikátem.|  
  
 Následující tabulka ukazuje výchozí chování pro každou zónu. Sloupec aplikace odkazuje na model Windows Forms aplikace, Windows Presentation Foundation aplikace, aplikace prohlížeče WPF a konzolové aplikace.  
  
|Zóna|Aplikace|řešení Office|  
|----------|------------------|----------------------|  
|`MyComputer`|`Enabled`|`Enabled`|  
|`LocalIntranet`|`Enabled`|`Enabled`|  
|`TrustedSites`|`Enabled`|`Enabled`|  
|`Internet`|`Enabled`|`AuthenticodeRequired`|  
|`UntrustedSites`|`Disabled`|`Disabled`|  
  
 Tato nastavení můžete přepsat povolením, omezením nebo zakázáním výzvy vztahu důvěryhodnosti ClickOnce.  
  
## <a name="enabling-the-clickonce-trust-prompt"></a>Povolení výzvy vztahu důvěryhodnosti ClickOnce  
 Pokud chcete, aby se koncovým uživatelům zobrazila možnost instalace a spuštění jakékoli aplikace ClickOnce, která pochází z této zóny, povolte výzvu k zadání vztahu důvěryhodnosti pro zónu.  
  
#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Povolení výzvy vztahu důvěryhodnosti ClickOnce pomocí Editoru registru  
  
1. Otevřete editor registru: .  
  
    1. Klikněte na tlačítko **Start**a potom na příkaz **Spustit**.  
  
    2. Do pole **otevřít** zadejte `regedit` (nebo `regedit32` v 32 Windows) a pak klikněte na **OK**.  
  
2. Vyhledejte následující klíč registru:  
  
     \ HKEY_LOCAL_MACHINE \SOFTWARE\MICROSOFT \\ . NETFramework\Security\TrustManager\PromptingLevel  
  
     Pokud klíč neexistuje, vytvořte ho.  
  
3. Přidejte následující podklíče jako **řetězcovou hodnotu**, pokud ještě neexistují, s přidruženými hodnotami, které jsou uvedeny v následující tabulce.  
  
    |Řetězcová hodnota – podklíč|Hodnota|  
    |-------------------------|-----------|  
    |`Internet`|`Enabled`|  
    |`UntrustedSites`|`Disabled`|  
    |`MyComputer`|`Enabled`|  
    |`LocalIntranet`|`Enabled`|  
    |`TrustedSites`|`Enabled`|  
  
     U řešení pro systém Office `Internet` má výchozí hodnotu `AuthenticodeRequired` a `UntrustedSites` má hodnotu `Disabled` . Pro všechny ostatní `Internet` má výchozí hodnotu `Enabled` .  
  
#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>Postup při povolení výzvy vztahu důvěryhodnosti ClickOnce programově  
  
1. Vytvořte Visual Basic nebo konzolovou aplikaci Visual C# v aplikaci Visual Studio.  
  
2. Otevřete soubor program. vb nebo Program.cs pro úpravy a přidejte následující kód.  
  
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
  
## <a name="restricting-the-clickonce-trust-prompt"></a>Omezení výzvy vztahu důvěryhodnosti pro ClickOnce  
 Omezte dotaz na vztah důvěryhodnosti, aby bylo možné řešení podepsat pomocí certifikátů Authenticode, které mají známou identitu před tím, než se uživatelům zobrazí výzva k rozhodnutí o důvěryhodnosti.  
  
#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Omezení výzvy vztahu důvěryhodnosti ClickOnce pomocí Editoru registru  
  
1. Otevřete editor registru: .  
  
    1. Klikněte na tlačítko **Start**a potom na příkaz **Spustit**.  
  
    2. Do pole **otevřít** zadejte `regedit` (nebo `regedit32` v 32 Windows) a pak klikněte na **OK**.  
  
2. Vyhledejte následující klíč registru:  
  
     \ HKEY_LOCAL_MACHINE \SOFTWARE\MICROSOFT \\ . NETFramework\Security\TrustManager\PromptingLevel  
  
     Pokud klíč neexistuje, vytvořte ho.  
  
3. Přidejte následující podklíče jako **řetězcovou hodnotu**, pokud ještě neexistují, s přidruženými hodnotami, které jsou uvedeny v následující tabulce.  
  
    |Řetězcová hodnota – podklíč|Hodnota|  
    |-------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`AuthenticodeRequired`|  
    |`MyComputer`|`AuthenticodeRequired`|  
    |`LocalIntranet`|`AuthenticodeRequired`|  
    |`TrustedSites`|`AuthenticodeRequired`|  
  
#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>Postup při programovému omezení výzvy vztahu důvěryhodnosti ClickOnce  
  
1. Vytvořte Visual Basic nebo konzolovou aplikaci Visual C# v aplikaci Visual Studio.  
  
2. Otevřete soubor program. vb nebo Program.cs pro úpravy a přidejte následující kód.  
  
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
  
## <a name="disabling-the-clickonce-trust-prompt"></a>Zakázání výzvy vztahu důvěryhodnosti ClickOnce  
 Můžete zakázat zobrazení výzvy vztahu důvěryhodnosti, aby koncoví uživatelé neměli možnost instalovat řešení, která ještě nejsou ve svých zásadách zabezpečení důvěryhodná.  
  
#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Zakázání výzvy vztahu důvěryhodnosti ClickOnce pomocí Editoru registru  
  
1. Otevřete editor registru: .  
  
    1. Klikněte na tlačítko **Start**a potom na příkaz **Spustit**.  
  
    2. Do pole **otevřít** zadejte `regedit` (nebo `regedit32` v 32 Windows) a pak klikněte na **OK**.  
  
2. Vyhledejte následující klíč registru:  
  
     \ HKEY_LOCAL_MACHINE \SOFTWARE\MICROSOFT \\ . NETFramework\Security\TrustManager\PromptingLevel  
  
     Pokud klíč neexistuje, vytvořte ho.  
  
3. Přidejte následující podklíče jako **řetězcovou hodnotu**, pokud ještě neexistují, s přidruženými hodnotami, které jsou uvedeny v následující tabulce.  
  
    |Řetězcová hodnota – podklíč|Hodnota|  
    |-------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`Disabled`|  
    |`MyComputer`|`Disabled`|  
    |`LocalIntranet`|`Disabled`|  
    |`TrustedSites`|`Disabled`|  
  
#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>Postup při programovém vypnutí výzvy vztahu důvěryhodnosti ClickOnce  
  
1. Vytvořte Visual Basic nebo konzolovou aplikaci Visual C# v aplikaci Visual Studio.  
  
2. Otevřete soubor program. vb nebo Program.cs pro úpravy a přidejte následující kód.  
  
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
 [Zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Zabezpečení přístupu ke kódu pro aplikace ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce a Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md)   
 [Postupy: povolení nastavení zabezpečení ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Postupy: nastavení zóny zabezpečení pro aplikaci ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Postupy: nastavení vlastních oprávnění pro aplikaci ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Postupy: ladění aplikace ClickOnce s omezenými oprávněními](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Postupy: Přidání důvěryhodného vydavatele do klientského počítače pro aplikace ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Postupy: Opětovné podepisování manifestů aplikace a nasazení](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
