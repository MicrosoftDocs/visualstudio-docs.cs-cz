---
title: Pomocí AspNetCompiler – úloha pro předkompilaci aplikace ASP.NET | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AspNetCompiler
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, AspNetCompiler task
- AspNetCompiler task [MSBuild]
ms.assetid: f811c019-a67b-4d54-82e6-e29549496f6e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 69971e72569dcae1f02f1e2b7988ef15f881fe85
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37945166"
---
# <a name="aspnetcompiler-task"></a>AspNetCompiler – úloha
`AspNetCompiler` Úkolů zabalí *aspnet_compiler.exe*, nástroj pro předkompilaci [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikací.  
  
## <a name="task-parameters"></a>Parametry úlohy  
 Následující tabulka popisuje parametry `AspNetCompiler` úloh.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`AllowPartiallyTrustedCallers`|Volitelné `Boolean` parametru.<br /><br /> Pokud je tento parametr `true`, bude sestavení se silným názvem povolovat částečně důvěryhodné volající.|  
|`Clean`|Volitelné `Boolean` parametr<br /><br /> Pokud je tento parametr `true`, bude předkompilovaná aplikace bude vytvořen čištění. Všechny již kompilované součásti budou znovu zkompilovány. Výchozí hodnota je `false`. Tento parametr **- c** zapnout *aspnet_compiler.exe*.|  
|`Debug`|Volitelné `Boolean` parametru.<br /><br /> Pokud je tento parametr `true`, informace o ladění (. Soubor PDB) je vygenerován v průběhu kompilace. Výchozí hodnota je `false`. Tento parametr **-d** zapnout *aspnet_compiler.exe*.|  
|`DelaySign`|Volitelné `Boolean` parametru.<br /><br /> Pokud je tento parametr `true`, po vytvoření není plně podepsáno sestavení.|  
|`FixedNames`|Volitelné `Boolean` parametru.<br /><br /> Pokud je tento parametr `true`, nedostanou zkompilovaným sestavením přiděleny pevně určené názvy...|  
|`Force`|Volitelné `Boolean` parametr<br /><br /> Pokud je tento parametr `true`, úloha se přepsat cílový adresář, pokud již existuje. Existující obsah bude ztracen. Výchozí hodnota je `false`. Tento parametr **-f** zapnout *aspnet_compiler.exe*.|  
|`KeyContainer`|Volitelné `String` parametru.<br /><br /> Určuje kontejner klíče se silným názvem.|  
|`KeyFile`|Volitelné `String` parametru.<br /><br /> Určuje fyzickou cestu k souboru klíče silného názvu...|  
|`MetabasePath`|Volitelné `String` parametru.<br /><br /> Určuje úplnou cestu metabáze služby IIS aplikace. Tento parametr se nedá kombinovat s `VirtualPath` nebo `PhysicalPath` parametry. Tento parametr **-m** zapnout *aspnet_compiler.exe*.|  
|`PhysicalPath`|Volitelné `String` parametru.<br /><br /> Určuje fyzickou cestu ke kompilaci aplikace. Pokud tento parametr chybí, metabáze služby IIS se používá k vyhledání aplikace. Tento parametr **-p** zapnout *aspnet_compiler.exe*.|  
|`TargetFrameworkMoniker`|Volitelné `String` parametru.<br /><br /> Určuje TargetFrameworkMoniker určující, která verze rozhraní .NET Framework *aspnet_compiler.exe* by měla sloužit. Přijímá pouze zástupných názvů rozhraní .NET Framework.|  
|`TargetPath`|Volitelné `String` parametru.<br /><br /> Určuje fyzickou cestu, do kterého bude uložena zkompilovaná aplikace. Pokud není zadán, aplikace je předkompilována místně.|  
|`Updateable`|Volitelné `Boolean` parametru.<br /><br /> Pokud je tento parametr `true`, bude předkompilovaná aplikace bude možné aktualizovat.  Výchozí hodnota je `false`. Tento parametr **-u** zapnout *aspnet_compiler.exe*.|  
|`VirtualPath`|Volitelné `String` parametru.<br /><br /> Virtuální cesta aplikace sestavují. Pokud `PhysicalPath` zadán, fyzickou cestu slouží k vyhledání aplikace. V opačném případě je použita metabáze služby IIS a aplikace se předpokládá se, že na výchozím webu. Tento parametr **- v** zapnout *aspnet_compiler.exe*.|  
  
## <a name="remarks"></a>Poznámky  
 Kromě výše uvedených parametrů zdědí tento úkol parametry ze <xref:Microsoft.Build.Tasks.ToolTaskExtension> třída, která sama dědí z <xref:Microsoft.Build.Utilities.ToolTask> třídy. Seznam těchto dalších parametrů a jejich popisy najdete v tématu [tooltaskextension – základní třída](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá `AspNetCompiler` úloh předkompilovat [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikace.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="PrecompileWeb">  
        <AspNetCompiler  
            VirtualPath="/MyWebSite"  
            PhysicalPath="c:\inetpub\wwwroot\MyWebSite\"  
            TargetPath="c:\precompiledweb\MyWebSite\"  
            Force="true"  
            Debug="true"  
        />  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Viz také:  
 [Úlohy](../msbuild/msbuild-tasks.md)   
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
