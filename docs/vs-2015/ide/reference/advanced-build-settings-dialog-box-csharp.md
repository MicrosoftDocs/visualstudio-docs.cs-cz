---
title: Dialogové okno Upřesnit nastavení sestavení (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.AdvancedBuildSettings
helpviewer_keywords:
- Build options [C#], advanced
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 38f4d233c8804bec91d2f7dfd2dc34c6879e8be9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651725"
---
# <a name="advanced-build-settings-dialog-box-c"></a>Dialogové okno Upřesnit nastavení sestavení (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pomocí dialogového okna **Nastavení AdvancedBuild** **Návrháře projektu** můžete zadat rozšířené vlastnosti konfigurace sestavení projektu. Toto dialogové okno se vztahuje [!INCLUDE[csprcs](../../includes/csprcs-md.md)] pouze na projekty.

## <a name="general"></a>Obecné
 Následující možnosti umožňují nastavit obecná Pokročilá nastavení.

 **Verze jazyka** Určuje verzi jazyka, který se má použít. Sada funkcí se v každé verzi liší, takže tuto možnost lze použít k vynucení, aby kompilátor povoloval pouze podmnožinu implementovaných funkcí, nebo aby povoloval pouze ty funkce, které jsou kompatibilní se stávajícím standardem. Toto nastavení má následující možnosti:

- **ISO-1**

   Cílí na standardní funkce ISO-1.

- **default**

   Cílí na aktuální verzi.

  Další informace naleznete v tématu [/langversion (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/3fb00b05-a0ff-4782-b313-13a4c0f62d94).

  **Zasílání zpráv o vnitřních chybách kompilátoru** Určuje, jestli se mají hlásit chyby kompilátoru Microsoftu. Pokud se nastaví **výzva** (výchozí nastavení), zobrazí se výzva, pokud dojde k vnitřní chybě kompilátoru, takže budete moct poslat zprávu o chybě elektronicky společnosti Microsoft. Pokud je nastavená na **Odeslat**, pošle se automaticky zpráva o chybě. Pokud je nastaveno na **Queue**, zprávy o chybách budou zařazeny do fronty. Pokud je nastavena na **hodnotu None**, bude chyba zaznamenána pouze v textovém výstupu kompilátoru. Další informace naleznete v tématu [/errorreport (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/bd0e7493-b79d-4369-9c3f-ba26ebdfbedf).

  **Kontrolovat aritmetické přetečení a podtečení** Určuje, zda je celočíselný aritmetický příkaz, který není v rozsahu [zkontrolovaných](https://msdn.microsoft.com/library/718a1194-988d-48a3-b089-d6ee8bd1608d) nebo [nekontrolovaných](https://msdn.microsoft.com/library/0c021f7c-923f-4b3d-a58f-55336f5ac27e) klíčových slov a který má za následek, že hodnota mimo rozsah datového typu způsobí výjimku za běhu. Další informace naleznete v tématu [/checked (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/fb7475d3-e6a6-4e6d-b86c-69e7a74c854b).

  **Neodkazovat na mscorlib.dll** Určuje, jestli se do programu naimportuje mscorlib.dll, a to tak, že se definuje celý <xref:System> obor názvů. Zaškrtněte toto políčko, pokud chcete definovat nebo vytvořit vlastní <xref:System> obor názvů a objekty. Další informace naleznete v tématu [/nostdlib (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/ec197989-fa49-4725-a455-e06b551eb65f).

## <a name="output"></a>Výstup
 Následující možnosti umožňují zadat upřesňující možnosti výstupu.

 **Informace o ladění** Určuje typ ladicích informací generovaných kompilátorem. Informace o tom, jak nakonfigurovat výkon ladění aplikace, najdete v tématu [Vytvoření obrázku pro snadnější ladění](https://msdn.microsoft.com/library/7d90ea7a-150f-4f97-98a7-f9c26541b9a3). Toto nastavení má následující možnosti:

- **žádný**

   Určuje, že se nevygenerují žádné informace o ladění.

- **kompletní**

   Umožňuje připojit k běžícímu programu ladicí program.

- **pdbonly**

   Umožňuje ladění zdrojového kódu, když je program spuštěn v ladicím programu, ale zobrazí pouze Assembler, pokud je spuštěný program připojen k ladicímu programu.

  Další informace naleznete v tématu [/Debug (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969).

  **Zarovnání souboru** Určuje velikost oddílů ve výstupním souboru. Platné hodnoty jsou **512**, **1024**, **2048**, **4096**a **8192**. Tyto hodnoty se měří v bajtech. Každý oddíl bude zarovnán na hranici, která je násobkem této hodnoty, což ovlivní velikost výstupního souboru. Další informace naleznete v tématu [/filealign (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/15cf1c98-3798-4ced-9f08-60619308a073).

  **Základní adresa knihovny DLL** Určuje upřednostňovanou základní adresu, na které se má načíst knihovna DLL. Výchozí základní adresa pro knihovnu DLL je nastavena modulem [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR (Common Language Runtime). Další informace naleznete v tématu [/BaseAddress (možnosti kompilátoru C#)](https://msdn.microsoft.com/library/ce13c965-dfe4-4433-94f5-63b476e3a608).

## <a name="see-also"></a>Viz také
 Stránka sestavení [možností kompilátoru C#](https://msdn.microsoft.com/library/d3403556-1816-4546-a782-e8223a772e44) [, Návrhář projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md)
