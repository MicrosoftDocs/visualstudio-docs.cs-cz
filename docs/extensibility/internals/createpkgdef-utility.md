---
title: Nástroj CreatePkgDef | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f437eb3586dc16bb0b4b9eb60cd303eb90db6c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709158"
---
# <a name="createpkgdef-utility"></a>Nástroj CreatePkgDef
Jako parametr provede soubor DLL pro příponu Visual Studio a vytvoří soubor *.pkgdef,* který bude doprovázet soubor *DLL.* Soubor *.pkgdef* obsahuje všechny informace, které by jinak byly zapsány do systémového registru při instalaci rozšíření.

> [!NOTE]
> Většina šablon projektu, které jsou součástí sady Visual Studio SDK, automaticky vytvoří soubory *.pkgdef* jako součást procesu sestavení. Tento dokument je určen pro ty, kteří chtějí vytvořit balíčky ručně nebo převést existující balíčky použít *.pkgdef* nasazení.

## <a name="syntax"></a>Syntaxe

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>Argumenty
**/out=&lt;Název_souboru&gt;**\
Povinná hodnota. Nastaví název výstupního souboru *.pkgdef* na &lt;Název_souboru&gt;.

**/codebase**\
Nepovinný parametr. Vynutí registraci pomocí nástroje **CodeBase.**

**/sestavení**\
Vynutí registraci pomocí nástroje **Shromáždění.**

**&lt;Cesta sestavení&gt;**\
Cesta k souboru *DLL,* ze kterého chcete vygenerovat *.pkgdef*.

## <a name="remarks"></a>Poznámky
Nasazení rozšíření pomocí souborů *.pkgdef* nahrazuje požadavky registru starších verzí sady Visual Studio.

::: moniker range=">=vs-2019"

Soubory *.pkgdef* musí být nainstalovány v jednom z následujících umístění:

- *%localappdata%\Microsoft\Visual Studio\16.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

Pokud je instalační složka *%localappdata%\Microsoft\Visual Studio\16.0\Extensions\\*, je rozšíření rozpoznáno aplikací Visual Studio, ale ve výchozím nastavení je zakázáno. Uživatel může rozšíření povolit pomocí **funkce Spravovat rozšíření**.

Pokud je instalační složka *%vsinstalldir%\Common7\IDE\Extensions\\*, je rozšíření ve výchozím nastavení povoleno.

> [!NOTE]
> Nástroj **Manage Extensions** nelze použít pro přístup k rozšíření, pokud není nainstalován jako součást balíčku VSIX.

::: moniker-end

::: moniker range="vs-2017"

Soubory *.pkgdef* musí být nainstalovány v jednom z následujících umístění:

- *%localappdata%\Microsoft\Visual Studio\15.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

Pokud je instalační složka *%localappdata%\Microsoft\Visual Studio\15.0\Extensions\\*, je rozšíření rozpoznáno aplikací Visual Studio, ale ve výchozím nastavení je zakázáno. Uživatel může povolit rozšíření pomocí **rozšíření a aktualizace**.

Pokud je instalační složka *%vsinstalldir%\Common7\IDE\Extensions\\*, je rozšíření ve výchozím nastavení povoleno.

> [!NOTE]
> **Nástroj Rozšíření a aktualizace** nelze použít pro přístup k rozšíření, pokud není nainstalován jako součást balíčku VSIX.

::: moniker-end

## <a name="see-also"></a>Viz také
- [Nástroj CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)
