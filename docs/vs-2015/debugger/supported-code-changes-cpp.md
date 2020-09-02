---
title: Podporované změny kódu (C++) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue, limitations
- supported code changes
- object files, limitations of Edit and Continue
- C++ language, supported code changes
- coding, supported code changes
- resource files, limitations of Edit and Continue
- code changes, handling in Edit and Continue
- what's new [C++], supported code changes
- code changes
ms.assetid: f5754363-8a56-417b-b904-b05d9dd26d03
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f167b3e9d27145284defa2ff491bb9ce0085f2a3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684911"
---
# <a name="supported-code-changes-c"></a>Podporované změny kódu (C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Upravit a pokračovat pro Visual C++ zpracovává většinu typů změn kódu. V průběhu provádění programu však nelze některé změny použít. Chcete-li tyto změny použít, je nutné zastavit provádění a vytvořit novou verzi kódu.  
  
 Informace o práci s úpravou a pokračováním pro jazyk C++ v aplikaci Visual Studio naleznete v tématu [Upravit a pokračovat (Visual C++)](../debugger/edit-and-continue-visual-cpp.md) .  
  
## <a name="unsupported-changes"></a><a name="BKMK_Unsupported_changes"></a> Nepodporované změny  

Následující změny jazyka C/C++ nelze použít během relace ladění:  
  
- Většina změn globálních nebo statických dat.  
  
- Změny spustitelných souborů, které jsou zkopírovány z jiného počítače a nejsou vytvořeny místně.  
  
- Změny datového typu, které ovlivňují rozložení objektu, například datových členů třídy.  
  
- Přidání více než 64kb bajtů nového kódu nebo dat.  
  
- Přidání proměnných, které vyžadují konstruktor v bodě před ukazatelem na instrukci.  
  
- Změny ovlivňující kód, který vyžaduje inicializaci za běhu.  
  
- Přidání obslužných rutin výjimek, v některých případech.  
  
- Změny souborů prostředků.  
  
- Změny kódu v souborech jen pro čtení.  
  
- Změny kódu bez odpovídajícího souboru PDB.  
  
- Změny kódu, který nemá žádný soubor objektu.  
  
Pokud uděláte jednu z těchto změn a pokusíte se použít změny kódu, zobrazí se v okně **výstup** chybová zpráva nebo zpráva s upozorněním.  
  
- Upravit a pokračovat neprovede aktualizace statických knihoven. Pokud provedete změnu ve statické knihovně, vykonání pokračuje ve staré verzi a nebude vydáno žádné upozornění.  
  
## <a name="unsupported-scenarios"></a><a name="BKMK_Unsupported_scenarios"></a> Nepodporované scénáře  
 Úpravy a pokračování pro C/C++ nejsou k dispozici v následujících scénářích ladění:  
  
- Ladění nativních aplikací kompilovaných pomocí [/Zo (rozšířené optimalizované ladění)](https://msdn.microsoft.com/library/eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f)  
  
- Ve verzích sady Visual Studio předcházejících aktualizaci Visual Studio 2015 Update 1, ladění aplikací nebo komponent pro Windows Store. Počínaje verzí Visual Studio 2015 Update 1 můžete použít příkaz Upravit a pokračovat v aplikacích pro Windows Store C++ a DirectX, protože teď podporuje `/ZI` přepínač kompilátoru s  `/bigobj` přepínačem. V případě binárních souborů kompilovaných s přepínačem můžete také použít možnost upravit a pokračovat `/FASTLINK` .  
  
- Ladění ve Windows 98.  
  
- Ladění ve smíšeném režimu (nativní/spravované)  
  
- Ladění JavaScriptu.  
  
- Ladění SQL.  
  
- Ladění souboru s výpisem paměti.  
  
- Úprava kódu po neošetřené výjimce, pokud není vybrána možnost **unwind zásobníku volání při neošetřených výjimkách** .  
  
- Ladění aplikace pomocí možnosti **připojit** místo spuštění aplikace, a to tak, že v nabídce **ladění** kliknete na možnost **Spustit** .  
  
- Ladění optimalizovaného kódu.  
  
- Ladění staré verze kódu po neúspěšném sestavení nové verze z důvodu chyb sestavení.  
  
## <a name="linking-limitations"></a><a name="BKMK_Linking_limitations"></a> Omezení propojení  
  
### <a name="linker-options-that-disable-edit-and-continue"></a><a name="BKMK_Linker_options_that_disable_Edit_and_Continue"></a> Možnosti linkeru, které zakazují úpravu a pokračování  
 Následující možnosti linkeru zakazují možnost upravit a pokračovat:  
  
- Nastavení **/OPT: ref**, **/OPT: ICF**nebo **/incremental: žádné** zakáže příkaz Upravit a pokračovat s následujícím upozorněním:  
  
     ODKAZ: upozornění LINKERŮ LNK4075: ignoruje se/EDITANDCONTINUE z důvodu/OPT  
  
     specifikace  
  
- Nastavením **/Order**, **/release**nebo **/Force** zakážete funkci upravit a pokračovat s tímto upozorněním:  
  
     ODKAZ: upozornění LINKERŮ LNK4075: ignoruje se/INCREMENTAL z důvodu/Option  
  
     specifikace  
  
- Nastavení jakékoli možnosti, která znemožňuje vytvoření souboru databáze programu (PDB), zakáže příkaz Upravit a pokračovat bez konkrétního upozornění.  
  
### <a name="auto-relinking-limitations"></a><a name="BKMK_Auto_relinking_limitations"></a> Omezení automatického přepojování  
 Ve výchozím nastavení příkaz Upravit a pokračovat znovu propojí na konci relace ladění a vytvoří aktuální spustitelný soubor.  
  
 Upravit a pokračovat nemůže znovu propojit program, pokud ho ladíte z jiného umístění, než je původní umístění sestavení. Zobrazí se zpráva s informacemi o tom, že je potřeba znovu sestavit ručně.  
  
 Při úpravě a pokračování nedojde k opakovanému sestavování statických knihoven. Pokud provedete změny statické knihovny pomocí upravit a pokračovat, budete muset ručně znovu sestavit knihovnu a znovu propojit aplikace, které ji používají.  
  
 Funkce Upravit a pokračovat nevyvolává vlastní kroky sestavení. Pokud program používá vlastní kroky sestavení, je nutné provést ruční opětovné sestavení, aby se vyvolaly vlastní kroky sestavení. V tom případě je možné vypnout propojování po funkci Upravit a pokračovat, aby bylo zaručeno, že budete vyzváni, abyste provedli ruční znovu sestavení.  
  
 **Zakázání přepojování po úpravě a pokračování**  
  
1. V nabídce **ladění** vyberte **Možnosti a nastavení**.  
  
2. V dialogovém okně **Možnosti** pod uzlem **ladění** a vyberte uzel **Upravit a pokračovat** .  
  
3. Zrušte zaškrtnutí políčka **znovu propojit změny kódu po ladění** .  
  
## <a name="precompiled-header-limitations"></a><a name="BKMK_Precompiled_Header_Limitations"></a> Omezení předkompilované hlavičky  
 Ve výchozím nastavení se při úpravách a pokračování načte a zpracovává předkompilovaných hlaviček na pozadí, aby se urychlilo zpracování změn kódu. Načtení předkompilovaných hlaviček vyžaduje přidělení fyzické paměti, což může být problém, pokud kompilujete na počítači s omezeným pamětí RAM. Můžete určit, zda se jedná o problém pomocí Správce úloh systému Windows k určení množství dostupné fyzické paměti při ladění. Pokud je tato hodnota vyšší než velikost předkompilovaných hlaviček, pak by funkce Upravit a pokračovat neměla mít problém. Pokud je velikost menší než velikost předkompilovaných hlaviček, můžete zabránit možnostem upravit a pokračovat v načítání předkompilovaných hlaviček na pozadí.  
  
 **Zakázání načítání předkompilovaných hlaviček na pozadí pro úpravy a pokračování**  
  
1. V nabídce **ladění** vyberte **Možnosti a nastavení**.  
  
2. V dialogovém okně **Možnosti** pod uzlem **ladění** a vyberte uzel **Upravit a pokračovat** .  
  
3. Zrušte zaškrtnutí políčka **Povol předkompilování** .  
  
## <a name="idl-attribute-limitations"></a><a name="BKMK_IDL_Attribute_Limitations"></a> Omezení atributů IDL  
 Upravit a pokračovat negeneruje znovu negenerované soubory definice rozhraní (IDL). Proto se změny atributů IDL nebudou odrazit při ladění. Chcete-li zobrazit výsledek změn atributů IDL, je nutné zastavit ladění a znovu sestavit aplikaci. Upravit a pokračovat negeneruje chybu nebo upozornění, pokud se změnily atributy IDL. Další informace naleznete v tématu [IDL – atributy](https://msdn.microsoft.com/library/04c596f4-c97b-4952-8053-316678b1d0b6).  
  
## <a name="see-also"></a>Viz také  
 [Upravit a pokračovat (Visual C++)](../debugger/edit-and-continue-visual-cpp.md)
