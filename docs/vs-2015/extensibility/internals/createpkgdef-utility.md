---
title: Nástroj CreatePkgDef | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 010ee75efd84f016b0eb68fa9f715102026a4678
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64782984"
---
# <a name="createpkgdef-utility"></a>Nástroj CreatePkgDef
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Převezme soubor. dll pro rozšíření aplikace Visual Studio jako parametr a vytvoří soubor. pkgdef, který bude doprovázet knihovnu DLL. Soubor. pkgdef obsahuje všechny informace, které by jinak byly zapsány do systémového registru při instalaci rozšíření.  
  
> [!NOTE]
> Většina šablon projektů, které jsou součástí sady Visual Studio SDK, automaticky vytvoří soubory. pkgdef jako součást procesu sestavení. Tento dokument je určený pro uživatele, kteří chtějí balíčky vytvořit ručně, nebo převeďte stávající balíčky na použití nasazení. pkgdef.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## <a name="arguments"></a>Argumenty  
 /out =`FileName`  
 Povinná hodnota. Nastaví název výstupního souboru. pkgdef na `FileName` .  
  
 /codebase  
 Nepovinný parametr. Vynutí registraci pomocí nástroje CodeBase.  
  
 /Assembly je  
 Vynutí registraci pomocí nástroje Assembly.  
  
 `AssemblyPath`  
 Cesta k souboru. dll, ze kterého chcete generovat soubor. pkgdef.  
  
## <a name="remarks"></a>Poznámky  
 Nasazení rozšíření pomocí souborů. pkgdef nahrazuje požadavky v registru dřívějších verzí sady Visual Studio.  
  
 Soubory. pkgdef musí být nainstalované v jednom z následujících umístění:%localappdata%\Microsoft\Visual Studio\14.0\Extensions\ nebo%vsinstalldir%\Common7\IDE\Extensions \\ . Pokud je instalační složka%localappdata%\Microsoft\Visual Studio\14.0\Extensions \\ , rozšíření rozpozná aplikace Visual Studio, ale ve výchozím nastavení bude zakázáno. Uživatel může rozšíření povolit pomocí **rozšíření a aktualizací**. Pokud je instalační složka%vsinstalldir%\Common7\IDE\Extensions \\ , je ve výchozím nastavení povolená přípona.  
  
> [!NOTE]
> Nástroj **rozšíření a aktualizace** nelze použít pro přístup k rozšíření, pokud není nainstalován jako součást balíčku VSIX.  
  
## <a name="see-also"></a>Viz také  
 [Nástroj CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)
