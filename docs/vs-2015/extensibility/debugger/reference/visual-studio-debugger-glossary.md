---
title: Glosář ladicího programu sady Visual Studio | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- glossary [Debugging SDK]
- debugging [Debugging SDK], glossary
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 37c0608b5684c9d16041ce89707dd81e665b0623
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757936"
---
# <a name="visual-studio-debugger-glossary"></a>Slovníček pro Visual Studio Debugger
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Následují termínů používaných v [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ladění sady SDK.  
  
## <a name="terms"></a>Podmínky  
 vázaná zarážka  
 Abstrakce pro zarážky nastavené v kódu. Existuje vztah 1: 1 mezi vázaná zarážka a instrukce zarážky v kódu. Pokud kód uvolní, může zrušení vazby zarážky vazby.  
  
 příčiny  
 Poskytuje možnost sledovat logické vlákno provádění v rámci více fyzických vláken, procesy a počítačů a k rekonstrukci tohoto logického vlákna v libovolném časovém okamžiku zásobníku volání během životnosti toto vlákno.  
  
 Kontext kódu  
 Poskytuje abstrakci na umístění v kódu známé ladicí stroj. Pro většinu za běhu architektury je kontext kódu adresa ve službě stream instrukce programu. Pro netradičních jazyky, ve kterých kód nemůže být reprezentována pokyny, mohou být zastoupeny kontext kódu jiným způsobem.  
  
 cesta kódu  
 Představuje bod provádění v kódu, ve kterém je větev nebo je provedeno volání funkce. Trasování zásobníku je v podstatě seznam cest kódu funkce volání.  
  
 ladicí stroj (DE)  
 Komponenta, která umožňuje ladění za běhu architektury. Ladicí stroj funguje ve spojení s překladač nebo operačního systému a poskytuje ladění služeb, jako je spouštění ovládacího prvku, zarážky a výraz hodnocení.  
  
 Kontext dokumentu  
 Poskytuje abstrakci pozice ve zdrojovém souboru dokumentu známé ladicí stroj. Většina jazyků je kontext dokumentu pozice ve zdrojovém souboru. Pro netradičních jazyky, pro které nemusí být zdrojový soubor text, může být reprezentován kontext dokumentu jiným způsobem. Viz také *pozice dokumentu*.  
  
 Pozice dokumentu  
 Poskytuje abstrakci pozice ve zdrojovém souboru ví, rozhraní IDE. Většina jazyků dokumentu pozice je pozice ve zdrojovém souboru. Netradičních jazyků může být reprezentován pozice dokumentu jinými způsoby. Viz také *kontext dokumentu*.  
  
 Chyba zarážky  
 Abstrakce pro popisující chybu v čekající zarážkou. K chybě zarážka může popisují chybu v umístění čekající zarážkou, výraz přidružený k čekající zarážka nebo Další informace, které brání čekající zarážka vazby do umístění kódu.  
  
 Kontext vyhodnocení  
 Poskytuje abstrakci programovacím kontextu pro vyhodnocování výrazů. Objekt context hodnocení je obvykle obor. Při provádění vyhodnocení výrazu v kontextu výrazu, poskytuje kontext Výraz pravidla rozsahu, které odpovídají jeho vytvoření. Například objekt context výraz vytvořené v rámci zásobníku obsahují souvislosti za vaše rozhodnutí vyzkoušet lokální proměnné, parametry metody, členy třídy (Pokud je k dispozici) a globální proměnné.  
  
 zachycené výjimky  
 Výjimka, která je zachycena ladicí stroj i v případě, že žádný mechanismus zpracování výjimek se používají v aktuální rámec zásobníku.  
  
 JustMyCode  
 Koncept ladění pouze kód, který patří uživateli a ignoruje všechny mezikódu, jako je například kód systému – i v případě, že zdrojový kód je k dispozici pro tento kód systému.  
  
 čekající zarážka  
 Poskytuje abstrakci pro zarážky před, během a po kód je načten a způsob, jak Virtualizovat zarážky. A až do zarážky:  
  
- Obsahuje všechny informace potřebné k vytvoření vazby zarážku do kódu v jedné nebo více programů.  
  
- Může vytvořit vazbu na několika místech kódu v jedné nebo více programů.  
  
- Nikdy vytvoří vazbu samotný kód.  
  
  Načte každý kódu v době, všech čekajících zarážek v programu zvoleny zobrazíte, pokud lze svázat. Čekající zarážka se říká, že obsahuje všechny vazby zarážky, které se váže.  
  
  zpracování  
  Fyzické proces Win32. Proces může obsahovat více programů. Viz také *program*.  
  
  program  
  Jeden obor názvů běží uvnitř konkrétní architektura za běhu. Viz také *procesu*.  
  
  Správce ladění relace (SDM)  
  Spravuje libovolný počet ladicími stroji ladění libovolný počet programy ve více procesech v libovolném počtu počítačů. Na úrovni basic je SDM multiplexor modulů ladění. Kromě toho SDM poskytuje jednotný přehled o relaci ladění do integrovaného vývojového prostředí.  
  
  rámec zásobníku  
  Představuje stav výpočet na konkrétní snímek a určitou úroveň volání vnořených funkcí.  
  
  vlákno  
  Zobecněný pojem instrukce založené na zásobníku spouštění používané alespoň jeden program.  
  
  upozornění zarážky  
  Abstrakce pro popis upozornění v čekající zarážkou. Upozornění zarážky popisuje důvod, proč čekající zarážka nebyla dosud vázán na místa v kódu. Je možné, že kód nenačetl ještě pro umístění popsal čekající zarážka nebo z nějakého důvodu.  
  
## <a name="see-also"></a>Viz také  
 [Rozšiřitelnost programu Visual Studio Debugger](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)

