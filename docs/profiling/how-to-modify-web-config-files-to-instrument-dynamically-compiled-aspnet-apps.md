---
title: 'Web.Config soubor: Nástroj & profil dynamické kompilované ASP.NET webové aplikace'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a92e5692-2183-4ae3-9431-b067c6a7aab4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 6fb67a5b0da186bd87b9e5c39204e3acccc0529f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775396"
---
# <a name="how-to-modify-webconfig-files-to-instrument-and-profile-dynamically-compiled-aspnet-web-applications"></a>Postup: Úprava souborů web.config na nástroj a profil dynamicky kompilované ASP.NET webových aplikací
Metodu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] instrumentace nástrojů profilování můžete použít ke shromažďování podrobných časovacích dat, dat přidělení [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] paměti .NET a dat životnosti objektu .NET z dynamicky zkompilovaných webových aplikací.

 Toto téma popisuje, jak upravit konfigurační soubor *web.config* tak, aby umožňoval instrumentaci a profilování webových [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikací.

> [!NOTE]
> Při použití metody vzorkování profilování nebo při nástroji předkompilovaného [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] modulu není nutné upravovat soubor *web.config.*

 Kořen souboru *web.config* je **konfigurační** prvek. Chcete-li instrumentovat a [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] profilovat dynamicky kompilovanou webovou aplikaci, musíte přidat nebo upravit následující prvky:

- Prvek **configuration/runtime/assemblyBinding/dependentAssemblyAssembly,** který identifikuje sestavení Microsoft.VisualStudio.Enterprise.ASPNetHelper, které řídí profilování. Prvek **dependentAssembly** obsahuje dva podřízené **prvky: assemblyIdentity** a **codeBase**.

- Prvek **configuration/system.web/compilation,** který identifikuje krok kompilace profileru po procesu pro cílové sestavení.

- Dva **prvky přidání,** které identifikují umístění nástrojů profilování, jsou přidány do oddílu **Konfigurace/appSettings** .

  Doporučujeme vytvořit kopii původního souboru *web.config,* který můžete použít k obnovení konfigurace aplikace.

### <a name="to-add-the-aspnethelper-assembly-as-a-configurationruntimeassemblybindingdependentassembly-element"></a>Přidání sestavení ASPNetHelper jako prvku configuration/runtime/assemblyBinding/dependentAssembly

1. V případě potřeby přidejte prvek **runtime** jako podřízený prvek **konfiguračního** prvku; v opačném případě přejděte k dalšímu kroku.

    Prvek **runtime** nemá žádné atributy. **Konfigurační** prvek může mít pouze jeden podřízený prvek **runtime.**

2. V případě potřeby přidejte element **assemblyBinding** jako podřízený prvek prvku **runtime;** v opačném případě přejděte k dalšímu kroku.

    **Runtime** element může mít pouze jeden element **assemblyBinding.**

3. Přidejte následující název atributu a hodnotu do elementu **assemblyBinding:**

   | Název atributu | Hodnota atributu |
   |----------------|--------------------------------------|
   | **Xmlns** | **urn:schémata-microsoft-com:asm.v1** |

4. Přidejte **prvek dependentAssembly** jako podřízený prvek elementu **assemblyBinding.**

    Prvek **dependentAssembly** nemá žádné atributy.

5. Přidejte element **assemblyIdentity** jako podřízený prvek **dependentAssembly.**

6. Do elementu assemblyIdentity přidejte následující **názvy atributů** a hodnoty:

   | Název atributu | Hodnota atributu |
   |--------------------| - |
   | **Jméno** | **Microsoft.VisualStudio.Enterprise.ASPNetHelper** |
   | **Publickeytoken** | **b03f5f7f11d50a3a** |
   | **jazyková verze** | **Neutral** |

7. Přidejte element **codeBase** jako podřízený prvek **dependentAssembly.**

8. Do elementu codeBase přidejte následující názvy a hodnoty **atributů:**

   |Název atributu|Hodnota atributu|
   |--------------------|---------------------|
   |**Verze**|**10.0.0.0**|
   |**Href**|`PathToASPNetHelperDll`|

    `PathToASPNetHelperDll`je adresa URL souboru souboru souboru Microsoft.VisualStudio.Enterprise.ASPNetHelper.dll. Pokud [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] je nainstalován ve výchozím umístění, hodnota **href** by měla být`C:/Program%20Files/Microsoft%20Visual%20Studio%202010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL`

```xml
    <configuration>
        <runtime>
            <assemblyBinding
                xmlns="urn:schemas-microsoft-com:asm.v1"
            >
                <dependentAssembly>
                    <assemblyIdentity name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"
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
```

### <a name="to-add-the-profiler-post-process-step-to-the-configurationsystemwebcompilation-element"></a>Přidání kroku profileru po procesu do prvku configuration/system.web/compilation

1. V případě potřeby přidejte element **system.web** jako podřízený prvek **konfiguračního** prvku; v opačném případě přejděte k dalšímu kroku.

     Element **system.web** nemá žádné atributy. **Konfigurační** prvek může mít pouze jeden podřízený prvek **system.web.**

2. V případě potřeby přidejte element **kompilace** jako podřízený prvek elementu **system.web;** v opačném případě přejděte k dalšímu kroku.

     Element **system.web** může mít pouze jeden podřízený prvek **kompilace.**

3. Odeberte všechny existující atributy z elementu **kompilace** a přidejte následující název atributu a hodnotu:

    |Název atributu|Hodnota atributu|
    |--------------------|---------------------|
    |**assemblyPostProcessorType**|**Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter, Microsoft.VisualStudio.Enterprise.ASPNetHelper, Version=10.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a**|

```xml
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

### <a name="to-add-profiler-location-settings-to-the-configurationappsettings-element"></a>Přidání nastavení umístění profileru do prvku configuration/appSettings

1. V případě potřeby přidejte element **appSettings** jako podřízený prvek **konfiguračního** prvku; v opačném případě přejděte k dalšímu kroku.

    Prvek **appSettings** nemá žádné atributy. **Konfigurační** prvek může mít pouze jeden podřízený prvek **appSettings.**

2. Přidejte element **add** jako podřízený prvek **appSettings.**

3. Do prvku **add** přidejte následující názvy atributů a hodnoty:

   | Název atributu | Hodnota atributu |
   |----------------| - |
   | **key** | **Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrUmístění** |
   | **Hodnotu** | `PerformanceToolsFolder`**\VSInstr.Exe** |

4. Přidejte další **prvek add** jako podřízený prvek **appSettings.**

5. Do tohoto **prvku add** přidejte následující názvy atributů a hodnoty:

   |Název atributu|Hodnota atributu|
   |--------------------|---------------------|
   |**key**|**Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools**|
   |**Hodnotu**|`PerformanceToolsFolder`|

    `PerformanceToolsFolder`je cesta spustitelných souborů profiler. Chcete-li získat cestu k nástrojům profilování, přečtěte si informace [o určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

```xml
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
                value="C:\Program Files\Microsoft Visual Studio 14.0\Team Tools\Performance Tools\vsinstr.exe"
        />
            <add
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"
                value="C:\Program Files\Microsoft Visual Studio 14.0\Team Tools\Performance Tools\"
            />
        </appSettings>
    </configuration>
```

## <a name="example"></a>Příklad
 Následuje kompletní soubor *web.config,* který umožňuje instrumentaci a profilování dynamicky kompilovaných [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webových aplikací. Tento příklad předpokládá, že před úpravou nebyly v souboru žádné další nastavení.

```xml
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
                value="C:\Program Files\Microsoft Visual Studio 14.0\Team Tools\Performance Tools\vsinstr.exe"
            />
            <add
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"
                value="C:\Program Files\Microsoft Visual Studio 14.0\Team Tools\Performance Tools\"
            />
        </appSettings>
    </configuration>

```

## <a name="see-also"></a>Viz také
- [Postup: Instrumentujte dynamicky sestavenou ASP.NET aplikaci a shromažďujte podrobné časovací údaje](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)
- [Postup: Instrumentujte dynamicky kompilované ASP.NET aplikace a shromažďujte paměťová data](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)
