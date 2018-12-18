---
title: 'Postupy: Konfigurace chování výzvy důvěryhodnosti ClickOnce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: wpickett
ms.openlocfilehash: f8fdb17bc724cc9cbf7385451a773a68ecf3df4e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49235661"
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>Postupy: Konfigurace chování výzvy důvěryhodnosti ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vztahu důvěryhodnosti ClickOnce pro ovládací prvek můžete nakonfigurovat, jestli koncovým uživatelům se zobrazí možnost instalace aplikace ClickOnce, jako je například aplikace Windows Forms, aplikace Windows Presentation Foundation, konzolové aplikace a prohlížeč WPF – aplikace a řešení pro systém Office. Konfigurace potvrzení důvěryhodnosti nastavením klíčů registru v počítači koncového uživatele.  
  
 V následující tabulce jsou uvedeny možnosti konfigurace, které lze použít u všech pět zóny (Internet, UntrustedSites, tento počítač, LocalIntranet a TrustedSites).  
  
|Možnost|Hodnota nastavení registru|Popis|  
|------------|----------------------------|-----------------|  
|Povolte výzvu vztahu důvěryhodnosti.|`Enabled`|Výzvy důvěryhodnosti ClickOnce je zobrazení tak, aby koncoví uživatelé můžou udělit důvěryhodnost aplikace ClickOnce.|  
|Omezte výzvu vztahu důvěryhodnosti.|`AuthenticodeRequired`|Výzvy důvěryhodnosti ClickOnce se zobrazí jenom v případě aplikace ClickOnce, které jsou podepsané certifikátem, který identifikuje vydavatele.|  
|Zakáže výzvu vztahu důvěryhodnosti.|`Disabled`|Výzvy důvěryhodnosti ClickOnce se nezobrazuje u všech aplikací ClickOnce, které nejsou podepsané explicitně důvěryhodný certifikát.|  
  
 V následující tabulce jsou uvedeny výchozí chování pro každou zónu. Sloupec aplikace odkazuje na aplikace Windows Forms, aplikace Windows Presentation Foundation, aplikací prohlížeče WPF a konzolové aplikace.  
  
|Zóna|Aplikace|řešení Office|  
|----------|------------------|----------------------|  
|`MyComputer`|`Enabled`|`Enabled`|  
|`LocalIntranet`|`Enabled`|`Enabled`|  
|`TrustedSites`|`Enabled`|`Enabled`|  
|`Internet`|`Enabled`|`AuthenticodeRequired`|  
|`UntrustedSites`|`Disabled`|`Disabled`|  
  
 Tato nastavení můžete přepsat povolením, omezení nebo zakázáním vztahu důvěryhodnosti ClickOnce.  
  
## <a name="enabling-the-clickonce-trust-prompt"></a>Povolení vztahu důvěryhodnosti ClickOnce  
 Povolte výzvu vztahu důvěryhodnosti pro zónu, když chcete koncovým uživatelům se zobrazí možnost instalace a spuštění jakékoli aplikace ClickOnce, která pochází z této zóny.  
  
#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Povolení vztahu důvěryhodnosti ClickOnce pomocí Editoru registru  
  
1.  Otevřete editor registru:  
  
    1.  Klikněte na tlačítko **Start**a potom klikněte na tlačítko **spustit**.  
  
    2.  V **otevřít** zadejte `regedit32`a potom klikněte na tlačítko **OK**.  
  
2.  Vyhledejte následující klíč registru:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel  
  
     Pokud klíč neexistuje, vytvořte ho.  
  
3.  Přidejte následující podklíče jako **řetězcovou hodnotu**, pokud ještě neexistují, s přiřazenými hodnotami, které jsou uvedeny v následující tabulce.  
  
    |Hodnota řetězce podklíče|Hodnota|  
    |-------------------------|-----------|  
    |`Internet`|`Enabled`|  
    |`UntrustedSites`|`Disabled`|  
    |`MyComputer`|`Enabled`|  
    |`LocalIntranet`|`Enabled`|  
    |`TrustedSites`|`Enabled`|  
  
     Pro řešení Office `Internet` má výchozí hodnotu `AuthenticodeRequired` a `UntrustedSites` má hodnotu `Disabled`. Pro všechny ostatní `Internet` má výchozí hodnotu `Enabled`.  
  
#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>Povolení vztahu důvěryhodnosti ClickOnce prostřednictvím kódu programu  
  
1.  Vytvoření konzolové aplikace v jazyce Visual Basic nebo Visual C# v sadě Visual Studio.  
  
2.  Otevřete soubor Program.vb nebo Program.cs soubor pro úpravy a přidejte následující kód.  
  
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
  
3.  Sestavte a spusťte aplikaci.  
  
## <a name="restricting-the-clickonce-trust-prompt"></a>Omezení vztahu důvěryhodnosti ClickOnce  
 Omezení výzvu vztahu důvěryhodnosti, takže řešení musí být podepsány pomocí technologie Authenticode certifikáty, které mají známé identity, než se uživatelům zobrazí výzva rozhodnutí důvěryhodnosti.  
  
#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Omezení vztahu důvěryhodnosti ClickOnce pomocí Editoru registru  
  
1.  Otevřete editor registru:  
  
    1.  Klikněte na tlačítko **Start**a potom klikněte na tlačítko **spustit**.  
  
    2.  V **otevřít** zadejte `regedit`a potom klikněte na tlačítko **OK**.  
  
2.  Vyhledejte následující klíč registru:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel  
  
     Pokud klíč neexistuje, vytvořte ho.  
  
3.  Přidejte následující podklíče jako **řetězcovou hodnotu**, pokud ještě neexistují, s přiřazenými hodnotami, které jsou uvedeny v následující tabulce.  
  
    |Hodnota řetězce podklíče|Hodnota|  
    |-------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`AuthenticodeRequired`|  
    |`MyComputer`|`AuthenticodeRequired`|  
    |`LocalIntranet`|`AuthenticodeRequired`|  
    |`TrustedSites`|`AuthenticodeRequired`|  
  
#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>Omezení vztahu důvěryhodnosti ClickOnce prostřednictvím kódu programu  
  
1.  Vytvoření konzolové aplikace v jazyce Visual Basic nebo Visual C# v sadě Visual Studio.  
  
2.  Otevřete soubor Program.vb nebo Program.cs soubor pro úpravy a přidejte následující kód.  
  
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
  
3.  Sestavte a spusťte aplikaci.  
  
## <a name="disabling-the-clickonce-trust-prompt"></a>Zakazuje zobrazení výzvy důvěryhodnosti ClickOnce  
 Výzvu vztahu důvěryhodnosti můžete zakázat, aby koncovým uživatelům se zobrazí možnost instalace řešení, které nejsou v jejich zásady zabezpečení již důvěryhodné.  
  
#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Chcete-li zakázat výzvy důvěryhodnosti ClickOnce pomocí Editoru registru  
  
1.  Otevřete editor registru:  
  
    1.  Klikněte na tlačítko **Start**a potom klikněte na tlačítko **spustit**.  
  
    2.  V **otevřít** zadejte `regedit`a potom klikněte na tlačítko **OK**.  
  
2.  Vyhledejte následující klíč registru:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel  
  
     Pokud klíč neexistuje, vytvořte ho.  
  
3.  Přidejte následující podklíče jako **řetězcovou hodnotu**, pokud ještě neexistují, s přiřazenými hodnotami, které jsou uvedeny v následující tabulce.  
  
    |Hodnota řetězce podklíče|Hodnota|  
    |-------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`Disabled`|  
    |`MyComputer`|`Disabled`|  
    |`LocalIntranet`|`Disabled`|  
    |`TrustedSites`|`Disabled`|  
  
#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>Chcete-li zakázat výzvy důvěryhodnosti ClickOnce prostřednictvím kódu programu  
  
1.  Vytvoření konzolové aplikace v jazyce Visual Basic nebo Visual C# v sadě Visual Studio.  
  
2.  Otevřete soubor Program.vb nebo Program.cs soubor pro úpravy a přidejte následující kód.  
  
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
  
3.  Sestavte a spusťte aplikaci.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečování aplikací ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Zabezpečení přístupu ke kódu pro aplikace ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce a kód Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md)   
 [Postupy: povolení nastavení zabezpečení ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Postupy: nastavení zóny zabezpečení pro aplikaci ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Postupy: nastavení vlastních oprávnění pro aplikaci ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Postupy: ladění aplikace ClickOnce s omezenými oprávněními](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Postupy: Přidání důvěryhodného vydavatele na klientský počítač pro aplikace ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Postupy: Opětovné podepisování manifestů aplikace a nasazení](../deployment/how-to-re-sign-application-and-deployment-manifests.md)



