---
title: Nástroj CreatePkgDef | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 47fee24292ee92b34cea6add21bc220a1a17f135
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49867660"
---
# <a name="createpkgdef-utility"></a>Nástroj CreatePkgDef
Vezme soubor .dll pro rozšíření sady Visual Studio jako parametr a vytvoří *.pkgdef* souboru vyvíjený *.dll* souboru. *.Pkgdef* soubor obsahuje všechny informace, které by jinak zapsat do systémového registru po instalaci rozšíření.  
  
> [!NOTE]
>  Většina šablon projektů, které jsou zahrnuty v sadě Visual Studio SDK automaticky vytvořit *.pkgdef* soubory jako součást procesu sestavení. Tento dokument je určený pro ty, kteří chtějí vytvořit balíčky ručně nebo převést existující balíčky používat *.pkgdef* nasazení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>  
```  
  
## <a name="arguments"></a>Arguments  
 **/ out =&lt;název souboru&gt;**  
 Požadováno. Nastaví název *.pkgdef* výstupní soubor &lt;FileName&gt;.  
  
 **/ codebase**  
 Volitelné. Vynutí registraci **CodeBase** nástroj.  
  
 **/ Assembly**  
 Vynutí registraci **sestavení** nástroj.  
  
 **&lt;AssemblyPath&gt;**  
 Cesta *.dll* soubor, ze kterého chcete generovat *.pkgdef*.  
  
## <a name="remarks"></a>Poznámky  
 Nasazení rozšíření pomocí *.pkgdef* soubory nahradí požadavky na registr starších verzí sady Visual Studio.  
  
 *.Pkgdef* soubory musí být nainstalovány v jednom z následujících umístění: 

- *%localappdata%\Microsoft\Visual Studio\14.0\Extensions\\* 
 
- *%VSInstallDir%\Common7\IDE\Extensions\\*
    
  Pokud je instalační složky sady *%localappdata%\Microsoft\Visual Studio\14.0\Extensions\\*, rozšíření rozpozná pomocí sady Visual Studio, ale bude ve výchozím nastavení zakázán. Uživatel můžete povolit rozšíření pomocí **rozšíření a aktualizace**. 
   
  Pokud je instalační složky sady *%vsinstalldir%\Common7\IDE\Extensions\\*, je rozšíření povoleno ve výchozím nastavení.  
  
> [!NOTE]
>  **Rozšíření a aktualizace** nástroj nelze použít pro přístup k rozšíření, pokud je nainstalován jako součást balíčku VSIX.  
  
## <a name="see-also"></a>Viz také:  
 [Nástroj CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)