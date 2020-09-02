---
title: Parametry vstupního bodu izolovaného prostředí (C++) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Shell [Visual Studio], isolated mode%2C Start entry point
- Visual Studio shell, isolated mode%2C Start entry point
ms.assetid: 18f4b18b-2173-4afa-ba0a-42fe33e61118
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9e736343212c4bf6acd833f5740b996c6c032c3f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64825151"
---
# <a name="isolated-shell-entry-point-parameters-c"></a>Parametry vstupních bodů izolovaného prostředí (C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Když se spustí aplikace založené na prostředí Visual Studio, zavolá počáteční vstupní bod prostředí Visual Studio. Následující nastavení lze přepsat voláním počátečního vstupního bodu prostředí. Popis jednotlivých nastavení naleznete v tématu [. Soubory pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
- AddinsAllowed  
  
- AllowsDroppedFilesOnMainWindow  
  
- AppName  
  
- CommandLineLogo  
  
- DefaultHomePage  
  
- DefaultProjectsLocation  
  
- DefaultSearchPage  
  
- DefaultUserFilesFolderRoot  
  
- DisableOutputWindow  
  
- HideMiscellaneousFilesByDefault  
  
- HideSolutionConcept  
  
- NewProjDlgInstalledTemplatesHdr  
  
- NewProjDlgSlnTreeNodeTitle  
  
- SolutionFileCreatorIdentifier  
  
- SolutionFileExt  
  
- UserFilesSubFolderName  
  
- UserOptsFileExt  
  
  Šablona izolovaného prostředí sady Visual Studio vytvoří zdrojový soubor, název *řešení*. cpp, kde název sady je *název řešení pro* aplikaci. Tento soubor definuje hlavní vstupní bod pro aplikaci, funkci _tWinMain. Tato funkce vyvolá počáteční vstupní bod prostředí.  
  
  Chování aplikace můžete změnit změnou těchto nastavení při spuštění aplikace.  
  
## <a name="parameters"></a>Parametry  
 Počáteční vstupní bod prostředí sady Visual Studio definuje pět parametrů. Neměňte první čtyři parametry. Pátý parametr přebírá seznam přepsání nastavení. Počáteční vstupní bod prostředí se volá z hlavního vstupního bodu aplikace.  
  
 Spouštěcí vstupní bod prostředí má následující podpis.  
  
```  
typedef int (__cdecl *STARTFCN)(LPSTR, LPWSTR, int, GUID *, WCHAR *pszSettings);  
```  
  
 Pokud nechcete přepsat žádná nastavení aplikace, ponechte hodnotu parametru přepsat nastavení jako ukazatel s hodnotou null.  
  
 Chcete-li přepsat jedno nebo více nastavení, předejte řetězec Unicode, který obsahuje nastavení, která mají být přepsána. Řetězec je seznam párů název-hodnota oddělený středníkem. Každý pár obsahuje název nastavení, které se má přepsat, následovaný symbolem rovná se (=) následovaný hodnotou, která se má použít pro nastavení.  
  
> [!NOTE]
> Do řetězců Unicode nezahrnujte prázdné znaky.  
  
 U logických nastavení představuje následující řetězce hodnotu true; všechny ostatní řetězce reprezentují hodnotu false. U těchto řetězců se nerozlišují malá a velká písmena.  
  
- \+  
  
- 1  
  
- -1  
  
- on  
  
- true  
  
- ano  
  
## <a name="example"></a>Příklad  
 Chcete-li zakázat doplňky a změnit výchozí umístění projektů pro vaši aplikaci, můžete nastavit poslední parametr na "AddinsAllowed = false; DefaultProjectsLocation =%USERPROFILE%\temp".  
  
## <a name="see-also"></a>Viz také  
 [Přizpůsobení izolovaného prostředí](../extensibility/customizing-the-isolated-shell.md)   
 [Soubory .Pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)
