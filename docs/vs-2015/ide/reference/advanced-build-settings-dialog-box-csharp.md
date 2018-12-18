---
title: Pokročilé dialogové okno nastavení sestavení (C#) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cs.AdvancedBuildSettings
helpviewer_keywords:
- Build options [C#], advanced
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9f3d62f6cd393dfccdaeb9047bac4780546f0087
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49811968"
---
# <a name="advanced-build-settings-dialog-box-c"></a>Dialogové okno Upřesnit nastavení sestavení (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Použití **AdvancedBuild nastavení** dialogovému oknu **Návrháře projektu** k určení rozšířenou vlastností konfigurace sestavení projektu. Toto dialogové okno se vztahuje na [!INCLUDE[csprcs](../../includes/csprcs-md.md)] pouze pro projekty.  
  
## <a name="general"></a>Obecné  
 Tyto možnosti umožňují nastavit obecné upřesňující nastavení.  
  
 **Verze jazyka**  
 Určuje verzi modulu jazyka. Sada funkcí se liší v jednotlivých verzích, proto tato možnost umožňuje vynutit na kompilátoru povolit pouze podmnožinu implementovaných funkcí nebo povolte jenom funkce, kompatibilní s současných standardů. Toto nastavení obsahuje následující možnosti:  
  
- **ISO-1**  
  
   Cíle standardních funkcí ISO-1.  
  
- **default**  
  
   Cílí na aktuální verzi.  
  
  Další informace najdete v tématu [/langversion (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/3fb00b05-a0ff-4782-b313-13a4c0f62d94).  
  
  **Vnitřní kompilátor zpráv o chybách**  
  Určuje, zda chcete zprávy o chybách kompilátoru společnosti Microsoft. Pokud nastavit **řádku** (výchozí), zobrazí se výzva Pokud dojde k chybě vnitřní kompilátor, získáte možnost elektronicky odešle zprávu o chybách společnosti Microsoft. Pokud hodnotu **odeslat**, zprávu o chybách se automaticky odešlou. Pokud hodnotu **fronty**, zprávy o chybách se zařadí do fronty. Pokud nastavena na **žádný**, ohlásí chybu pouze v kompilátoru textový výstup. Další informace najdete v tématu [/errorreport (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/bd0e7493-b79d-4369-9c3f-ba26ebdfbedf).  
  
  **Kontrolovat aritmetické přetečení a podtečení**  
  Určuje, zda celočíselný aritmetické příkaz, který není v oboru [zaškrtnutí](http://msdn.microsoft.com/library/718a1194-988d-48a3-b089-d6ee8bd1608d) nebo [Nekontrolovaná](http://msdn.microsoft.com/library/0c021f7c-923f-4b3d-a58f-55336f5ac27e) klíčová slova a způsobí, že výsledkem je hodnota mimo rozsah datového typu za běhu došlo k výjimce. Další informace najdete v tématu [/ checked (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/fb7475d3-e6a6-4e6d-b86c-69e7a74c854b).  
  
  **Neodkazovat na mscorlib.dll**  
  Určuje, zda mscorlib.dll se naimportují do programu, definování celý <xref:System> oboru názvů. Toto políčko zaškrtněte, pokud chcete definovat nebo si vytvořte svoje vlastní <xref:System> obor názvů a objekty. Další informace najdete v tématu [/nostdlib (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/ec197989-fa49-4725-a455-e06b551eb65f).  
  
## <a name="output"></a>Výstup  
 Tyto možnosti umožňují zadat možnosti pokročilé výstupu.  
  
 **Informace o ladění**  
 Určuje typ ladicích informací generovaných kompilátorem. Informace o tom, jak konfigurovat výkon ladění aplikace najdete v tématu [usnadnění bitové kopie k ladění](http://msdn.microsoft.com/library/7d90ea7a-150f-4f97-98a7-f9c26541b9a3). Toto nastavení obsahuje následující možnosti:  
  
- **None**  
  
   Určuje, že se nevygeneruje žádná informace o ladění  
  
- **Úplné**  
  
   Umožňuje připojení ladicího programu ke spuštěnému programu.  
  
- **pdbonly**  
  
   Umožňuje zdrojového kódu, ladění, když program se spustí v ladicím programu, ale zobrazí jenom assembler když spuštěný program je připojen k ladicímu programu.  
  
  Další informace najdete v tématu [/Debug (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969).  
  
  **Zarovnání souboru**  
  Určuje velikost oddíly výstupního souboru. Platné hodnoty jsou **512**, **1024**, **2048**, **4096**, a **8192**. Tyto hodnoty se měří v bajtech. Každý oddíl se zarovnáno na hranici, která je násobkem tuto hodnotu by to ovlivnilo velikost výstupního souboru. Další informace najdete v tématu [/filealign (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/15cf1c98-3798-4ced-9f08-60619308a073).  
  
  **Základní adresa knihovny DLL**  
  Určuje upřednostňovaná základní adresa, ve kterém se má načíst knihovnu DLL. Výchozí základní adresa pro knihovnu DLL se nastavuje [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] společného jazykového modulu runtime. Další informace najdete v tématu [/BaseAddress (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/ce13c965-dfe4-4433-94f5-63b476e3a608).  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru C#](http://msdn.microsoft.com/library/d3403556-1816-4546-a782-e8223a772e44)   
 [Stránka Sestavení, Návrhář projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md)



