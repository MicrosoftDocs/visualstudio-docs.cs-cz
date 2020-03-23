---
title: Úloha signfile | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#SignFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, SignFile task
- SignFile task [MSBuild]
ms.assetid: edef1819-ddeb-4e09-95de-fc7063ba9388
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ee018b42fc23b0a520b510235117cb74729fd4b6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094517"
---
# <a name="signfile-task"></a>SignFile – úloha

Podepisuje zadaný soubor pomocí zadaného certifikátu.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `SignFile` úkolu.

 Všimněte si, že certifikáty SHA-256 jsou povoleny pouze na počítačích, které mají .NET 4.5 a vyšší.

> [!WARNING]
> Počínaje Visual Studio 2013 Update 3, tato úloha má nový podpis, který umožňuje zadat verzi cílového rozhraní pro soubor. Doporučujeme použít nový podpis všude tam, kde je to možné, protože proces MSBuild používá hashe sha-256 pouze v případě, že cílový rámec je .NET 4.5 nebo vyšší. Pokud je cílová architektura .NET 4.0 nebo nižší, hašiš SHA-256 nebude použit.

|Parametr|Popis|
|---------------|-----------------|
|`CertificateThumbprint`|Požadovaný parametr `String`.<br /><br /> Určuje certifikát, který má být používán k podepisování. Tento certifikát musí být v osobním úložišti aktuálního uživatele.|
|`SigningTarget`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje soubory, které se mají podepisovat certifikátem.|
|`TimestampUrl`|Volitelný `String` parametr.<br /><br /> Určuje adresu URL serveru časového razítka.|
|`TargetFrameworkVersion`|Verze rozhraní .NET Framework, která se používá pro cíl.|

## <a name="remarks"></a>Poznámky

 Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Utilities.Task> parametry z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [Základní třída úlohy](../msbuild/task-base-class.md).

## <a name="example"></a>Příklad

 Následující příklad používá `SignFile` úkol k podepsání `FilesToSign` souborů určených v kolekci položek s certifikátem určeným vlastností. `CertificateThumbprint`

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <FileToSign Include="File.exe" />
    </ItemGroup>
    <PropertyGroup>
        <Certificate>Cert.cer</Certificate>
    </PropertyGroup>
    <Target Name="Sign">
        <SignFile
            CertificateThumbprint="$(CertificateThumbprint)"
            SigningTarget="@(FileToSign)"
            TargetFrameworkVersion="v4.5" />
    </Target>
</Project>
```

> [!NOTE]
> Kryptografický otisk certifikátu je hash SHA-1 certifikátu. Další informace naleznete [v tématu Získání hash sha-1 důvěryhodného kořenového certifikátu certifikační autority](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc733076\(v\=ws.10\)). Pokud zkopírujete a vložíte kryptografický otisk z podrobností o certifikátu, ujistěte `SignFile` se, že neobsahujete další (3F) neviditelný znak, který může zabránit v nalezení certifikátu.

## <a name="see-also"></a>Viz také

- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Úlohy](../msbuild/msbuild-tasks.md)