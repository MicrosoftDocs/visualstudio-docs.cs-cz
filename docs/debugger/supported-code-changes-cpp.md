---
title: Podporované změny kódu (C++) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: b93c9cfa6767aea83d941cbc8684b27517c8f911
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729552"
---
# <a name="supported-code-changes-c"></a>Podporované změny kódu (C++)
Upravit a pokračovat pro C++ projekty zpracovává většinu typů změn kódu. V průběhu provádění programu však nelze některé změny použít. Chcete-li tyto změny použít, je nutné zastavit provádění a vytvořit novou verzi kódu.

 Informace o práci s úpravou a pokračováním C++ v aplikaci Visual Studio naleznete v tématu [Upravit a pokračovat (C++)](../debugger/edit-and-continue-visual-cpp.md) .

## <a name="BKMK_Unsupported_changes"></a>Nepodporované změny
 Během relace ladění nelzeC++ použít následující C/změny:

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

## <a name="BKMK_Unsupported_scenarios"></a>Nepodporované scénáře
 Upravit a pokračovat pro C/C++ není k dispozici v následujících scénářích ladění:

- Ladění nativních aplikací kompilovaných pomocí [/Zo (rozšířené optimalizované ladění)](/cpp/build/reference/zo-enhance-optimized-debugging)

- Ve verzích sady Visual Studio předcházejících aktualizaci Visual Studio 2015 Update 1 ladí aplikace nebo komponenty UWP. Počínaje verzí Visual Studio 2015 Update 1 můžete použít možnost upravit a pokračovat v aplikacích pro C++ UWP a DirectX, protože teď podporuje přepínač kompilátoru `/ZI` s přepínačem `/bigobj`. Můžete také použít příkaz Upravit a pokračovat v binárních souborech kompilovaných s přepínačem `/FASTLINK`.

- Ladění ve Windows 98.

- Ladění ve smíšeném režimu (nativní/spravované)

- Ladění JavaScriptu.

- Ladění SQL.

- Ladění souboru s výpisem paměti.

- Úprava kódu po neošetřené výjimce, pokud není vybrána možnost **unwind zásobníku volání při neošetřených výjimkách** .

- Ladění aplikace pomocí možnosti **připojit** místo spuštění aplikace, a to tak, že v nabídce **ladění** kliknete na možnost **Spustit** .

- Ladění optimalizovaného kódu.

- Ladění staré verze kódu po neúspěšném sestavení nové verze z důvodu chyb sestavení.

## <a name="BKMK_Linking_limitations"></a>Omezení propojení

### <a name="BKMK_Linker_options_that_disable_Edit_and_Continue"></a>Možnosti linkeru, které zakazují úpravu a pokračování
 Následující možnosti linkeru zakazují možnost upravit a pokračovat:

- Nastavení **/OPT: ref**, **/OPT: ICF**nebo **/incremental: žádné** zakáže příkaz Upravit a pokračovat s následujícím upozorněním:

     ODKAZ: upozornění LINKERŮ LNK4075: ignoruje se/EDITANDCONTINUE z důvodu/OPT

     specifikace

- Nastavením **/Order**, **/release**nebo **/Force** zakážete funkci upravit a pokračovat s tímto upozorněním:

     ODKAZ: upozornění LINKERŮ LNK4075: ignoruje se/INCREMENTAL z důvodu/Option

     specifikace

- Nastavení jakékoli možnosti, která znemožňuje vytvoření souboru databáze programu (PDB), zakáže příkaz Upravit a pokračovat bez konkrétního upozornění.

### <a name="BKMK_Auto_relinking_limitations"></a>Omezení automatického přepojování
 Ve výchozím nastavení příkaz Upravit a pokračovat znovu propojí na konci relace ladění a vytvoří aktuální spustitelný soubor.

 Upravit a pokračovat nemůže znovu propojit program, pokud ho ladíte z jiného umístění, než je původní umístění sestavení. Zobrazí se zpráva s informacemi o tom, že je potřeba znovu sestavit ručně.

 Při úpravě a pokračování nedojde k opakovanému sestavování statických knihoven. Pokud provedete změny statické knihovny pomocí upravit a pokračovat, budete muset ručně znovu sestavit knihovnu a znovu propojit aplikace, které ji používají.

 Funkce Upravit a pokračovat nevyvolává vlastní kroky sestavení. Pokud program používá vlastní kroky sestavení, je nutné provést ruční opětovné sestavení, aby se vyvolaly vlastní kroky sestavení. V tom případě je možné vypnout propojování po funkci Upravit a pokračovat, aby bylo zaručeno, že budete vyzváni, abyste provedli ruční znovu sestavení.

 **Zakázání přepojování po úpravě a pokračování**

1. V nabídce **ladění** vyberte **Možnosti a nastavení**.

2. V dialogovém okně **Možnosti** pod uzlem **ladění** a vyberte uzel **Upravit a pokračovat** .

3. Zrušte zaškrtnutí políčka **znovu propojit změny kódu po ladění** .

## <a name="BKMK_Precompiled_Header_Limitations"></a>Omezení předkompilované hlavičky
 Ve výchozím nastavení se při úpravách a pokračování načte a zpracovává předkompilovaných hlaviček na pozadí, aby se urychlilo zpracování změn kódu. Načtení předkompilovaných hlaviček vyžaduje přidělení fyzické paměti, což může být problém, pokud kompilujete na počítači s omezeným pamětí RAM. Můžete určit, zda se jedná o problém pomocí Správce úloh systému Windows k určení množství dostupné fyzické paměti při ladění. Pokud je tato hodnota vyšší než velikost předkompilovaných hlaviček, pak by funkce Upravit a pokračovat neměla mít problém. Pokud je velikost menší než velikost předkompilovaných hlaviček, můžete zabránit možnostem upravit a pokračovat v načítání předkompilovaných hlaviček na pozadí.

 **Zakázání načítání předkompilovaných hlaviček na pozadí pro úpravy a pokračování**

1. V nabídce **ladění** vyberte **Možnosti a nastavení**.

2. V dialogovém okně **Možnosti** pod uzlem **ladění** a vyberte uzel **Upravit a pokračovat** .

3. Zrušte zaškrtnutí políčka **Povol předkompilování** .

## <a name="BKMK_IDL_Attribute_Limitations"></a>Omezení atributů IDL
 Upravit a pokračovat negeneruje znovu negenerované soubory definice rozhraní (IDL). Proto se změny atributů IDL nebudou odrazit při ladění. Chcete-li zobrazit výsledek změn atributů IDL, je nutné zastavit ladění a znovu sestavit aplikaci. Upravit a pokračovat negeneruje chybu nebo upozornění, pokud se změnily atributy IDL. Další informace naleznete v tématu [IDL – atributy](/cpp/windows/idl-attributes).

## <a name="see-also"></a>Viz také:
- [Upravit a pokračovat (C++)](../debugger/edit-and-continue-visual-cpp.md)