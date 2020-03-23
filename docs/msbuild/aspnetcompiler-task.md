---
title: Předkompilace ASP.NET aplikacích pomocí úlohy AspNetCompiler Task | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 8707371fac876586d38f12a797aaee7228b5f729
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634575"
---
# <a name="aspnetcompiler-task"></a>AspNetCompiler – úloha

Úloha `AspNetCompiler` zalomí *aspnet_compiler.exe*, nástroj pro předkompilaci ASP.NET aplikací.

## <a name="task-parameters"></a>Parametry úlohy

Následující tabulka popisuje parametry `AspNetCompiler` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`AllowPartiallyTrustedCallers`|Volitelný `Boolean` parametr.<br /><br /> Pokud je `true`tento parametr ,, sestavení silného názvu umožní částečně důvěryhodné volající.|
|`Clean`|Volitelný `Boolean` parametr<br /><br /> Pokud tento `true`parametr je , předkompilované aplikace budou vytvořeny čisté. Všechny dříve zkompilované součásti budou znovu zkompilovány. Výchozí hodnota je `false`. Tento parametr odpovídá přepínači **-c** na *aspnet_compiler.exe*.|
|`Debug`|Volitelný `Boolean` parametr.<br /><br /> Pokud je `true`tento parametr , ladění informací (. PDB) je emitován během kompilace. Výchozí hodnota je `false`. Tento parametr odpovídá přepínači **-d** na *aspnet_compiler.exe*.|
|`DelaySign`|Volitelný `Boolean` parametr.<br /><br /> Pokud je `true`tento parametr , sestavení není plně podepsána při vytvoření.|
|`FixedNames`|Volitelný `Boolean` parametr.<br /><br /> Pokud je `true`tento parametr , zkompilovaná sestavení budou mít pevné názvy..|
|`Force`|Volitelný `Boolean` parametr<br /><br /> Pokud je `true`tento parametr , úkol přepíše cílový adresář, pokud již existuje. Existující obsah jsou ztraceny. Výchozí hodnota je `false`. Tento parametr odpovídá přepínači **-f** na *aspnet_compiler.exe*.|
|`KeyContainer`|Volitelný `String` parametr.<br /><br /> Určuje kontejner klíčů silného názvu.|
|`KeyFile`|Volitelný `String` parametr.<br /><br /> Určuje fyzickou cestu k souboru klíče silného názvu.|
|`MetabasePath`|Volitelný `String` parametr.<br /><br /> Určuje úplnou cestu metabázi služby IIS aplikace. Tento parametr nelze kombinovat `VirtualPath` s `PhysicalPath` parametry nebo. Tento parametr odpovídá přepínači **-m** na *aspnet_compiler.exe*.|
|`PhysicalPath`|Volitelný `String` parametr.<br /><br /> Určuje fyzickou cestu aplikace, která má být kompilována. Pokud tento parametr chybí, metabase služby IIS se používá k vyhledání aplikace. Tento parametr odpovídá přepínači **-p** na *aspnet_compiler.exe*.|
|`TargetFrameworkMoniker`|Volitelný `String` parametr.<br /><br /> Určuje targetframeworkmoniker označující, která verze *rozhraní .NET Framework aspnet_compiler.exe* by měla být použita. Přijímá pouze zástupné názvy rozhraní .NET Framework.|
|`TargetPath`|Volitelný `String` parametr.<br /><br /> Určuje fyzickou cestu, ke které je aplikace kompilována. Pokud není zadán, aplikace je předkompilován na místě.|
|`Updateable`|Volitelný `Boolean` parametr.<br /><br /> Pokud je `true`tento parametr , bude možné předkompilovat aplikaci aktualizovat.  Výchozí hodnota je `false`. Tento parametr odpovídá přepínači **-u** na *aspnet_compiler.exe*.|
|`VirtualPath`|Volitelný `String` parametr.<br /><br /> Virtuální cesta aplikace, která má být kompilována. Pokud `PhysicalPath` je zadán, fyzická cesta se používá k vyhledání aplikace. V opačném případě se použije metabáze služby IIS a předpokládá se, že aplikace je ve výchozí lokalitě. Tento parametr odpovídá přepínači **-v** na *aspnet_compiler.exe*.|

## <a name="remarks"></a>Poznámky

Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.ToolTaskExtension> parametry z třídy, <xref:Microsoft.Build.Utilities.ToolTask> která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [ToolTaskExtension base class](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Příklad

Následující příklad kódu `AspNetCompiler` používá úlohu k předkompilaci ASP.NET aplikace.

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

## <a name="see-also"></a>Viz také

* [Úlohy](../msbuild/msbuild-tasks.md)
* [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
