---
title: 'Postupy: Úprava souborů Web.Config za účelem instrumentace a profilování dynamicky kompilovaných webových aplikací ASP.NET | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a92e5692-2183-4ae3-9431-b067c6a7aab4
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f668bebb2967ca89feb1c6f52f00253ac3eb07b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807748"
---
# <a name="how-to-modify-webconfig-files-to-instrument-and-profile-dynamically-compiled-aspnet-web-applications"></a>Postupy: Úprava souborů Web.Config za účelem instrumentace a profilování dynamicky kompilovaných webových aplikací ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete použít [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nástrojů pro profilaci sady metody instrumentace ke shromažďování podrobných dat časování, data o přidělování paměti .NET a životnosti objektů .NET z dynamicky zkompilován [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webové aplikace.  
  
 Toto téma popisuje, jak upravit konfigurační soubor web.config pro povolení instrumentace a profilování [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webové aplikace.  
  
> [!NOTE]
>  Není nutné upravit soubor web.config, použijete-li metoda profilování vzorkování nebo instrumentaci předkompilované [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] modulu.  
  
 Je kořenový soubor web.config **konfigurace** elementu. Účelem instrumentace a profilování dynamicky kompilovaných [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webovou aplikaci, musíte přidat nebo upravit následující prvky:  
  
- A **konfigurace/runtime/assemblyBinding/dependentAssembly** element, který identifikuje Microsoft.VisualStudio.Enterprise.ASPNetHelper sestavení, které ovládací prvky, profilování. **DependentAssembly** prvek obsahuje dva podřízené prvky: **assemblyIdentity** a **codeBase**.  
  
- A **configuration/system.web/compilation** element, který identifikuje krok následného zpracování kompilace profileru pro cílové sestavení.  
  
- Dvě **přidat** prvky, které určují umístění nástroje pro profilaci sady nástrojů se přidávají do **konfigurace/appSettings** oddílu.  
  
  Doporučujeme vytvořit kopii původního souboru web.config, který můžete použít k obnovení nastavení aplikace.  
  
### <a name="to-add-the-aspnethelper-assembly-as-a-configurationruntimeassemblybindingdependentassembly-element"></a>Chcete-li přidat ASPNetHelper sestavení jako konfigurace/runtime/assemblyBinding/dependentAssembly – element  
  
1.  V případě potřeby přidat **runtime** prvek jako podřízený prvek **konfigurace** prvek; v opačném případě přejděte k dalšímu kroku.  
  
     **Runtime** prvek nemá žádné atributy. **Konfigurace** prvek může mít pouze jeden **runtime** podřízený element.  
  
2.  V případě potřeby přidat **assemblyBinding** prvek jako podřízený prvek **runtime** prvek; v opačném případě přejděte k dalšímu kroku.  
  
     **Runtime** prvek může mít pouze jeden **assemblyBinding** elementu.  
  
3.  Přidejte následující atribut název a hodnota, která se **assemblyBinding** element:  
  
    |Název atributu|Hodnota atributu|  
    |--------------------|---------------------|  
    |**xmlns.**|**název urn: schémata-microsoft-com:asm.v1**|  
  
4.  Přidat **dependentAssembly** prvek jako podřízený prvek **assemblyBinding** elementu.  
  
     **DependentAssembly** prvek nemá žádné atributy.  
  
5.  Přidat **assemblyIdentity** element jako podřízený objekt **dependentAssembly** elementu.  
  
6.  Přidejte následující atribut názvy a hodnoty, které mají **assemblyIdentity** element:  
  
    |Název atributu|Hodnota atributu|  
    |--------------------|---------------------|  
    |**Jméno**|**Microsoft.VisualStudio.Enterprise.ASPNetHelper**|  
    |**PublicKeyToken**|**b03f5f7f11d50a3a**|  
    |**Jazyková verze**|**Neutrální**|  
  
7.  Přidat **základu kódu** element jako podřízený objekt **dependentAssembly** elementu.  
  
8.  Přidejte následující atribut názvy a hodnoty, které mají **codeBase** element:  
  
    |Název atributu|Hodnota atributu|  
    |--------------------|---------------------|  
    |**version**|**10.0.0.0**|  
    |**href**|`PathToASPNetHelperDll`|  
  
     `PathToASPNetHelperDll` je adresa URL souboru Microsoft.VisualStudio.Enterprise.ASPNetHelper.dll. Pokud [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] je nainstalován do výchozího umístění **href** hodnota by měla být `C:/Program%20Files/Microsoft%20Visual%20Studio%202010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL`  
  
```  
    <configuration>  
        <runtime>  
            <assemblyBinding   
                xmlns="urn:schemas-microsoft-com:asm.v1"  
            >  
                <dependentAssembly>  
                    <assemblyIdentity                         name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"   
                        publicKeyToken="b03f5f7f11d50a3a"                         culture="neutral"   
                    />  
                    <codeBase   
                        version="10.0.0.0"  
                        href="file:///C:/Program%20Files/Microsoft%20Visual%20Studio%2010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL"   
                    />  
                </dependentAssembly>  
            </assemblyBinding>  
        </runtime>  
```  
  
### <a name="to-add-the-profiler-post-process-step-to-the-configurationsystemwebcompilation-element"></a>Můžete přidat krok následného zpracování Profiler configuration/system.web/compilation element  
  
1.  V případě potřeby přidat **system.web** prvek jako podřízený prvek **konfigurace** prvek; v opačném případě přejděte k dalšímu kroku.  
  
     **System.web** prvek nemá žádné atributy. **Konfigurace** prvek může mít pouze jeden **system.web** podřízený element.  
  
2.  V případě potřeby přidat **kompilace** prvek jako podřízený prvek **system.web** prvek; v opačném případě přejděte k dalšímu kroku.  
  
     **System.web** prvek může mít pouze jeden **kompilace** podřízený element.  
  
3.  Odeberte všechny existující atributy z **kompilace** prvek a přidejte následující atribut název a hodnotu:  
  
    |Název atributu|Hodnota atributu|  
    |--------------------|---------------------|  
    |**assemblyPostProcessorType**|**Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter Microsoft.VisualStudio.Enterprise.ASPNetHelper, verze = 10.0.0.0, Culture = neutral, PublicKeyToken = b03f5f7f11d50a3a**|  
  
```  
    <configuration>  
        <runtime>  
        . . .  
        </runtime>  
        <system.web>  
            <compilation  
                assemblyPostProcessorType="Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter,  
                    Microsoft.VisualStudio.Enterprise.ASPNetHelper,  
                    Version=10.0.0.0,  
                    Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"   
            />  
        </system.web>  
    <configuration>  
```  
  
### <a name="to-add-profiler-location-settings-to-the-configurationappsettings-element"></a>Chcete-li přidat nastavení umístění Profiler element konfigurace/appSettings  
  
1.  V případě potřeby přidat **appSettings** prvek jako podřízený prvek **konfigurace** prvek; v opačném případě přejděte k dalšímu kroku.  
  
     **AppSettings** prvek nemá žádné atributy. **Konfigurace** prvek může mít pouze jeden **appSettings** podřízený element.  
  
2.  Přidat **přidat** element jako podřízený objekt **appSettings** elementu.  
  
3.  Přidejte následující atribut názvy a hodnoty, které mají **přidat** element:  
  
    |Název atributu|Hodnota atributu|  
    |--------------------|---------------------|  
    |**Klíč**|**Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation**|  
    |**value**|`PerformanceToolsFolder` **\VSInstr.exe**|  
  
4.  Přidejte další **přidat** element jako podřízený objekt **appSettings** elementu.  
  
5.  Přidejte následující atribut názvy a hodnoty tohoto **přidat** element:  
  
    |Název atributu|Hodnota atributu|  
    |--------------------|---------------------|  
    |**Klíč**|**Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools**|  
    |**value**|`PerformanceToolsFolder`|  
  
     `PerformanceToolsFolder` je cesta profileru spustitelné soubory. Pokud [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] je nainstalovaný ve výchozím umístění, bude hodnota **10.0\Team C:\Program Files\Microsoft Visual Studio Tools nástroje**  
  
```  
    <configuration>  
        <runtime>  
        . . .  
        </runtime>  
        . . .  
        <system.web>  
        </system.web>  
        <appSettings>  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\vsinstr.exe"  
        />  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\"  
            />  
        </appSettings>  
    </configuration>  
```  
  
## <a name="example"></a>Příklad  
 Tady je úplný web.config soubor, který umožní instrumentace a profilování dynamicky kompilovaných [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webové aplikace. Tento příklad předpokládá, že neexistují žádná ostatní nastavení v souboru před provedením změny.  
  
```  
<?xml version="1.0"?>  
    <configuration>  
        <runtime>  
            <assemblyBinding   
                xmlns="urn:schemas-microsoft-com:asm.v1"  
            >  
                <dependentAssembly>  
                    <assemblyIdentity   
                        name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"   
                        publicKeyToken="b03f5f7f11d50a3a"  
                        culture="neutral"   
                    />  
                    <codeBase   
                        version="10.0.0.0"  
                        href="file:///C:/Program%20Files/Microsoft%20Visual%20Studio%2010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL"   
                    />  
                </dependentAssembly>  
            </assemblyBinding>  
        </runtime>  
        <system.web>  
            <compilation  
                assemblyPostProcessorType="Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter,  
                    Microsoft.VisualStudio.Enterprise.ASPNetHelper,  
                    Version=10.0.0.0,  
                    Culture=neutral,  
                    PublicKeyToken=b03f5f7f11d50a3a"   
            />  
        </system.web>  
        <appSettings>  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\vsinstr.exe"  
            />  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\"  
            />  
        </appSettings>  
    </configuration>  
  
```  
  
## <a name="see-also"></a>Viz také  
 [Postupy: instrumentace dynamicky kompilované ASP.NET aplikace a shromažďování podrobných dat časování](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)   
 [Postupy: Instrumentace dynamicky kompilované aplikace ASP.NET a shromáždění dat paměti](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)



