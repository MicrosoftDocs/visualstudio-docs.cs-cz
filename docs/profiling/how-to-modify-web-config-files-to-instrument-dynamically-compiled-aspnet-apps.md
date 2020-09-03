---
title: Web.Config dynamické zkompilované webové aplikace ASP.NET pro & profilování souborů
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: a92e5692-2183-4ae3-9431-b067c6a7aab4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 8ed2d8e8cc62d26f9d63a8a675301c78fc35c51a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85331508"
---
# <a name="how-to-modify-webconfig-files-to-instrument-and-profile-dynamically-compiled-aspnet-web-applications"></a>Postupy: Změna web.config souborů pro instrumentaci a profilování dynamicky kompilovaných webových aplikací ASP.NET
Pomocí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] metody instrumentace nástroje pro profilaci můžete shromažďovat podrobná data časování, data o přidělování paměti .NET a data o životnosti objektů .NET z dynamicky kompilovaných [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webových aplikací.

 Toto téma popisuje, jak upravit konfigurační soubor *web.config* pro povolení instrumentace a profilování [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webových aplikací.

> [!NOTE]
> Při použití metody profilace vzorkování nebo v případě, že chcete instrumentovat předem kompilovaný modul, není nutné upravovat *web.config* soubor [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] .

 Kořen *web.config* souboru je **konfigurační** element. Chcete-li instrumentovat a profilovat dynamicky kompilované [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webové aplikace, je nutné přidat nebo upravit následující prvky:

- Element **Configuration/runtime/assemblyBinding/dependentAssembly** , který identifikuje sestavení Microsoft. VisualStudio. Enterprise. ASPNetHelper, které řídí profilaci. Element **dependentAssembly** obsahuje dva podřízené elementy: **assemblyIdentity** a **základ kódu**.

- Element **Configuration/System. web/compilation** , který identifikuje krok následného procesu kompilace profileru pro cílové sestavení.

- Do části **Configuration/appSettings** se přidají dva prvky **Přidat** , které identifikují umístění nástrojů nástroje pro profilaci.

  Doporučujeme vytvořit kopii původního souboru *web.config* , který můžete použít k obnovení konfigurace aplikace.

### <a name="to-add-the-aspnethelper-assembly-as-a-configurationruntimeassemblybindingdependentassembly-element"></a>Přidání sestavení ASPNetHelper jako konfiguračního/běhového prvku/assemblyBinding/dependentAssembly

1. V případě potřeby přidejte **běhový** element jako podřízený prvek **konfiguračního** elementu; v opačném případě pokračujte na další krok.

    **Běhový** element nemá žádné atributy. Prvek **Konfigurace** může mít pouze jeden podřízený element **modulu runtime** .

2. V případě potřeby přidejte element **assemblyBinding** jako podřízený element elementu **runtime** ; v opačném případě pokračujte na další krok.

    **Běhový** element může mít pouze jeden element **assemblyBinding** .

3. Do prvku **assemblyBinding** přidejte následující název a hodnotu atributu:

   | Název atributu | Hodnota atributu |
   |----------------|--------------------------------------|
   | **Xmlns** | **urn: schemas-microsoft-com: asm. v1** |

4. Přidejte prvek **dependentAssembly** jako podřízený prvek elementu **assemblyBinding** .

    Element **dependentAssembly** nemá žádné atributy.

5. Přidejte prvek **assemblyIdentity** jako podřízený prvek **dependentAssembly** .

6. Přidejte následující názvy atributů a hodnoty do prvku **assemblyIdentity** :

   | Název atributu | Hodnota atributu |
   |--------------------| - |
   | **Jméno** | **Microsoft. VisualStudio. Enterprise. ASPNetHelper** |
   | **PublicKeyToken** | **b03f5f7f11d50a3a** |
   | **jazykových** | **Jazyk** |

7. Přidejte element **codebase** jako podřízený prvek **dependentAssembly** .

8. Přidejte následující názvy atributů a hodnoty do prvku **codebase** :

   |Název atributu|Hodnota atributu|
   |--------------------|---------------------|
   |**znění**|**sítě**|
   |**odkaz**|`PathToASPNetHelperDll`|

    `PathToASPNetHelperDll` je adresa URL souboru Microsoft.VisualStudio.Enterprise.ASPNetHelper.dll. Pokud [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] je aplikace nainstalována ve výchozím umístění, měla by být hodnota **href**`C:/Program%20Files/Microsoft%20Visual%20Studio%202010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL`

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

### <a name="to-add-the-profiler-post-process-step-to-the-configurationsystemwebcompilation-element"></a>Přidání kroku následného procesu profileru do prvku Configuration/System. web/compilation

1. V případě potřeby přidejte element **System. Web** jako podřízený prvek **konfiguračního** elementu; v opačném případě pokračujte na další krok.

     Element **System. Web** nemá žádné atributy. Prvek **Konfigurace** může mít pouze jeden podřízený element **System. Web** .

2. V případě potřeby přidejte element **compilation** jako podřízený element elementu **System. Web** ; v opačném případě pokračujte na další krok.

     Element **System. Web** může mít pouze jeden podřízený element **compilation** .

3. Odeberte všechny existující atributy z prvku **compilation** a přidejte následující název a hodnotu atributu:

    |Název atributu|Hodnota atributu|
    |--------------------|---------------------|
    |**assemblyPostProcessorType**|**Microsoft. VisualStudio. Enterprise. Common. AspPerformanceInstrumenter, Microsoft. VisualStudio. Enterprise. ASPNetHelper, Version = 10.0.0.0, Culture = neutral, PublicKeyToken = b03f5f7f11d50a3a**|

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

### <a name="to-add-profiler-location-settings-to-the-configurationappsettings-element"></a>Přidání nastavení umístění profileru do prvku Configuration/appSettings

1. V případě potřeby přidejte element **appSettings** jako podřízený prvek **konfiguračního** elementu; v opačném případě pokračujte na další krok.

    Element **appSettings** nemá žádné atributy. Prvek **Konfigurace** může mít pouze jeden podřízený element **appSettings** .

2. Přidejte element **Add** jako podřízený prvek **appSettings** .

3. Přidejte následující názvy atributů a hodnoty do elementu **Add** :

   | Název atributu | Hodnota atributu |
   |----------------| - |
   | **zkrat** | **Microsoft. VisualStudio. Enterprise. AspNetHelper. VsInstrLocation** |
   | **osa** | `PerformanceToolsFolder`**\VSInstr.Exe** |

4. Přidejte další element **Add** jako podřízený prvek **appSettings** .

5. Do tohoto elementu **Add** přidejte následující názvy atributů a hodnoty:

   |Název atributu|Hodnota atributu|
   |--------------------|---------------------|
   |**zkrat**|**Microsoft. VisualStudio. Enterprise. AspNetHelper. VsInstrTools**|
   |**osa**|`PerformanceToolsFolder`|

    `PerformanceToolsFolder` je cesta ke spustitelným souborům profileru. Postup získání cesty k nástrojům pro profilaci najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

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
 Následuje kompletní soubor *web.config* , který umožňuje instrumentaci a profilování dynamicky kompilovaných [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webových aplikací. V tomto příkladu se předpokládá, že v souboru nejsou žádné další nastavení před úpravou.

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
- [Postupy: instrumentace dynamicky kompilované aplikace ASP.NET a shromažďování podrobných dat časování](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)
- [Postupy: instrumentace dynamicky kompilované aplikace ASP.NET a shromažďování dat paměti](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)
