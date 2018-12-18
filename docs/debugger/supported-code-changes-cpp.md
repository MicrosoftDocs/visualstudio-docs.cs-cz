---
title: Podporované změny kódu (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue, limitations
- supported code changes
- object files, limitations of Edit and Continue
- C# language, supported code changes
- coding, supported code changes
- resource files, limitations of Edit and Continue
- code changes, handling in Edit and Continue
- what's new [C#], supported code changes
- code changes
ms.assetid: f5754363-8a56-417b-b904-b05d9dd26d03
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: c1d4333014f63bec73c13b3a7b1d5f9c7d59697f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49854114"
---
# <a name="supported-code-changes-c"></a>Podporované změny kódu (C++)
Upravit a pokračovat jazyka Visual C++ zpracovává většinu typů změn kódu. Nicméně některé změny nejde použít při provádění programu. Pokud chcete tyto změny použít, musíte zastavit provádění a vytvářet nové verze kódu.  
  
 Zobrazit [upravit a pokračovat (Visual C++)](../debugger/edit-and-continue-visual-cpp.md) informace o práci s upravit a pokračovat jazyka C++ v sadě Visual Studio.  
  
##  <a name="BKMK_Unsupported_changes"></a> Nepodporované změny  
 Následující změny C/C++ nemohou být provedeny během relace ladění:  
  
- Většina změn globální nebo statická data.  
  
- Změny spustitelné soubory, které jsou zkopírovány z jiného počítače a nebyl sestaven místně.  
  
- Změny na datový typ, které ovlivňují rozložení objektu, například datové členy třídy.  
  
- Přidání více než 64 kB nový kód nebo data.  
  
- Přidání proměnné, které vyžadují konstruktor v okamžiku před ukazatele na instrukci.  
  
- Změny, které ovlivňují kód, který vyžaduje inicializace za běhu.  
  
- Přidání obslužných rutin výjimek, v některých případech.  
  
- Změny v souborech prostředků.  
  
- Změny kódu v souborech jen pro čtení.  
  
- Změny kódu bez odpovídajícího souboru PDB.  
  
- Změny kódu, který nemá žádný soubor objektu.  
  
  Pokud jeden z těchto změn a pokuste se použít změny kódu, chyby nebo upozornění se zobrazí v **výstup** okna.  
  
- Upravit a pokračovat se neaktualizuje statických knihoven. Pokud provedete změny ve statické knihovně, provádění pokračuje ve starší verzi a žádné upozornění.  
  
##  <a name="BKMK_Unsupported_scenarios"></a> Nepodporované scénáře  
 Upravit a pokračovat pro C/C++ není k dispozici v následujících scénářích ladění:  
  
-   Ladění nativní aplikace kompilována s [/Zo (vylepšit optimalizované ladění)](/cpp/build/reference/zo-enhance-optimized-debugging)  
  
-   Ve verzích sady Visual Studio před Visual Studio 2015 Update 1, ladění aplikací pro UWP nebo komponenty. Od verze Visual Studio 2015 Update 1, můžete upravit a pokračovat v UWP C++ a aplikací rozhraní DirectX, protože teď podporuje `/ZI` přepínač kompilátoru se `/bigobj` přepnout. Můžete také upravit a pokračovat s binárními soubory zkompilovaná `/FASTLINK` přepnout.  
  
-   Ladění na Windows 98.  
  
-   Ladění ve smíšeném režimu (nativní a spravovaná).  
  
-   Ladění jazyka JavaScript.  
  
-   Ladění SQL.  
  
-   Ladění souboru výpisu paměti.  
  
-   Úpravy kódu po neošetřené výjimky, když **vrátit zásobník volání v případě neošetřených výjimek** možnost není vybraná.  
  
-   Ladění aplikace s použitím **připojit k** místo spouštění aplikace výběrem **Start** na **ladění** nabídky.  
  
-   Ladění optimalizovaného kódu.  
  
-   Ladění starou verzi kódu po nové verze se nepovedlo sestavit kvůli chybám sestavení.  
  
##  <a name="BKMK_Linking_limitations"></a> Omezení propojení  
  
###  <a name="BKMK_Linker_options_that_disable_Edit_and_Continue"></a> Možnosti linkeru, které zákaz operace upravit a pokračovat  
 Následující možnosti linkeru zákaz operace upravit a pokračovat:  
  
-   Nastavení **OPT**, **/OPT:ICF**, nebo **/incremental: No** zakáže upravit a pokračovat s následujícím upozorněním:  
  
     ODKAZ: upozornění LNK4075: ignoruje se neignoruje kvůli/OPT  
  
     specifikace  
  
-   Nastavení **/ORDER**, **/RELEASE**, nebo **/FORCE** zakáže upravit a pokračovat se toto upozornění:  
  
     ODKAZ: upozornění LNK4075: ignoruje se parametr/incremental kvůli/Option  
  
     specifikace  
  
-   Nastavení možnosti, které brání vytvoření souboru databáze (PDB) programu zakáže upravit a pokračovat v žádné konkrétní upozornění.  
  
###  <a name="BKMK_Auto_relinking_limitations"></a> Automatického opakovaného propojování omezení  
 Ve výchozím nastavení upravit a pokračovat relinks programu na konci vytvoří spustitelný aktuální relace ladění.  
  
 Upravit a pokračovat nemůže znovu programu, pokud ladíte z jiného umístění než původní umístění sestavení. Zobrazí se zpráva, že je potřeba ručně znovu sestavit.  
  
 Upravit a pokračovat není znovu sestavit statických knihoven. Pokud provedete změny na statickou knihovnu použitím funkce upravit a pokračovat, budete muset ručně znovu vytvořit knihovnu a znovu připojit aplikace používat.  
  
 Funkce Upravit a pokračovat nevyvolává vlastní kroky sestavení. Pokud program používá vlastní kroky sestavení, je nutné provést ruční opětovné sestavení, aby se vyvolaly vlastní kroky sestavení. V tom případě je možné vypnout propojování po funkci Upravit a pokračovat, aby bylo zaručeno, že budete vyzváni, abyste provedli ruční znovu sestavení.  
  
 **Chcete-li zakázat opakovaného propojování po funkci upravit a pokračovat**  
  
1.  Na **ladění** nabídce zvolte **možnosti a nastavení**.  
  
2.  V **možnosti** dialogovém okně **ladění** uzel a vyberte **upravit a pokračovat** uzlu.  
  
3.  Zrušte **po ladění znovu propojit změny kódu** zaškrtávací políčko.  
  
##  <a name="BKMK_Precompiled_Header_Limitations"></a> Omezení předkompilované hlavičky  
 Ve výchozím nastavení upravit a pokračovat zatížení a procesy předkompilované hlavičky pro zrychlení zpracování změn kódu na pozadí. Načtení předkompilovaných hlaviček vyžaduje alokaci fyzické paměti, což může být problém, pokud kompilace probíhá na počítači s omezeným množstvím paměti RAM. Můžete určit, pokud to může být problém s použitím Správce úloh Windows ke zjištění dostupné fyzické paměti během ladění. Pokud je tato hodnota vyšší než velikost předkompilovaných hlaviček, pak by funkce Upravit a pokračovat neměla mít problém. Pokud je tato hodnota menší než velikost předkompilovaných hlaviček, můžete zabránit upravit a pokračovat v načtení předkompilovaných hlaviček na pozadí.  
  
 **Chcete-li zakázat načítání předkompilovaných hlaviček na pozadí pro funkce upravit a pokračovat**  
  
1.  Na **ladění** nabídce zvolte **možnosti a nastavení**.  
  
2.  V **možnosti** dialogovém okně **ladění** uzel a vyberte **upravit a pokračovat** uzlu.  
  
3.  Zrušte **povolit předkompilování** zaškrtávací políčko.  
  
##  <a name="BKMK_IDL_Attribute_Limitations"></a> Omezení atributu IDL  
 Upravit a pokračovat neobnoví soubory rozhraní definice (IDL). Proto se změny IDL – atributy neprojeví během ladění. Pokud chcete zobrazit výsledek změny IDL – atributy, musí zastavit ladění a znovu sestavte aplikaci. Upravit a pokračovat nevygeneruje chybu nebo upozornění Pokud se změnily atributy IDL. Další informace najdete v tématu [IDL – atributy](/cpp/windows/idl-attributes).  
  
## <a name="see-also"></a>Viz také  
 [Upravit a pokračovat (Visual C#)](../debugger/edit-and-continue-visual-cpp.md)