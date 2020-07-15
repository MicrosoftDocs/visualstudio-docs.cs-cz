---
title: Úloha SignFile – | Microsoft Docs
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
ms.openlocfilehash: 319afb810ba755d0201d3edaebcb06a493b59047
ms.sourcegitcommit: c2b3bf0de44cd379fd1ad5110385021d0ec950ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/14/2020
ms.locfileid: "86301444"
---
# <a name="signfile-task"></a>SignFile – úloha

Podepíše zadaný soubor pomocí zadaného certifikátu.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `SignFile` úkolu.

 Certifikáty SHA-256 jsou povoleny pouze v počítačích s rozhraním .NET 4,5 a vyšším.

> [!WARNING]
> Počínaje Visual Studio 2013 Update 3 má tento úkol nový podpis, který umožňuje zadat cílovou verzi rozhraní .NET Framework pro daný soubor. Pokud je to možné, doporučujeme používat nový podpis, protože proces MSBuild používá hodnoty hash SHA-256 pouze v případě, že je cílovým rozhraním .NET 4,5 nebo vyšší. Pokud je cílová architektura rozhraní .NET 4,0 nebo nižší, nebude použita hodnota hash SHA-256.

|Parametr|Popis|
|---------------|-----------------|
|`CertificateThumbprint`|Požadovaný parametr `String`.<br /><br /> Určuje certifikát, který se má použít pro podepisování. Tento certifikát se musí nacházet v osobním úložišti aktuálního uživatele.|
|`SigningTarget`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje soubory, které mají být podepsány certifikátem typu. exe nebo. dll.|
|`TimestampUrl`|Volitelný `String` parametr.<br /><br /> Určuje adresu URL serveru časového razítka.|
|`TargetFrameworkVersion`|Verze .NET Framework, která se používá pro cíl.|

## <a name="remarks"></a>Poznámky

 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popisů naleznete v tématu [základní třída Task](../msbuild/task-base-class.md).

## <a name="example"></a>Příklad

 Následující příklad používá `SignFile` úlohu k podepsání souborů zadaných v `FilesToSign` kolekci Item s certifikátem zadaným `CertificateThumbprint` vlastností.

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
> Kryptografický otisk certifikátu je hodnota hash SHA-1 certifikátu. Další informace najdete v tématu [získání hodnoty hash SHA-1 certifikátu důvěryhodné kořenové certifikační autority](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc733076\(v\=ws.10\)). Pokud zkopírujete a vložíte kryptografický otisk z podrobností certifikátu, ujistěte se, že nezahrnete znak extra (3F) neviditelný, což by mohlo bránit `SignFile` v hledání certifikátu.

## <a name="see-also"></a>Viz také

- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
- [Úlohy](../msbuild/msbuild-tasks.md)