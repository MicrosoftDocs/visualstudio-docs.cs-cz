---
title: Doporučené postupy pro používání fragmentů kódu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code snippets, best practices
- code snippets, security
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 08add20b59e3e14897d1870aa45fd6cce8698d96
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591707"
---
# <a name="best-practices-for-using-code-snippets"></a>Doporučené postupy pro použití fragmentů kódu

Kód ve fragmentu kódu zobrazuje pouze nejzákladnější způsob, jak něco provést. Pro většinu aplikací musí být kód upraven tak, aby vyhovoval aplikaci.

## <a name="handling-exceptions"></a>Zpracování výjimek

Fragment kódu obvykle zkuste... Catch bloky zachytit a znovu vyvolat všechny výjimky. To nemusí být správná volba pro váš projekt. Pro každou výjimku existuje několik způsobů, jak reagovat. Příklady najdete v [tématu Jak: Zpracování výjimky pomocí try/catch (C#)](/dotnet/csharp/programming-guide/exceptions/how-to-handle-an-exception-using-try-catch) a [Zkuste... Chytit... Finally příkaz (Visual Basic)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement).

## <a name="file-locations"></a>Umístění souborů

Při přizpůsobování umístění souborů aplikaci byste měli přemýšlet o následujících:

- Hledání přístupného místa. Uživatelé nemusí mít přístup ke složce *Program Files* v počítači, takže ukládání souborů se soubory aplikace nemusí fungovat.

- Najít bezpečné místo. Ukládání souborů do kořenové složky (*C:\\*) není bezpečné. Pro data aplikace doporučujeme složku *Data aplikace.* Pro jednotlivá uživatelská data může aplikace vytvořit soubor pro každého uživatele ve složce *Dokumenty.*

- Použití platného názvu souboru. Ovládací prvky <xref:System.Windows.Forms.OpenFileDialog> <xref:System.Windows.Forms.SaveFileDialog> a můžete použít ke snížení pravděpodobnosti neplatných názvů souborů. Uvědomte si, že mezi časem, kdy uživatel vybere soubor, a časem, kdy váš kód manipuluje se souborem, může být soubor odstraněn. Kromě toho uživatel nemusí mít oprávnění k zápisu do souboru.

## <a name="security"></a>Zabezpečení

Jak zabezpečený fragment je závisí na tom, kde se používá ve zdrojovém kódu a jak je upraven, jakmile je v kódu. Následující seznam obsahuje několik oblastí, které je třeba vzít v úvahu.

- Přístup k souborům a databázi

- Zabezpečení přístupu kódu

- Ochrana prostředků (například protokoly událostí, registr)

- Ukládání tajemství

- Ověřování vstupů

- Předávání dat skriptovacím technologiím

Další informace naleznete v [tématu Zabezpečení aplikací](../ide/securing-applications.md).

## <a name="downloaded-code-snippets"></a>Stažené fragmenty kódu

Fragmenty kódu IntelliSense nainstalované aplikací Visual Studio samy o sobě nepředstavují bezpečnostní riziko. Mohou však vytvářet bezpečnostní rizika ve vaší aplikaci. S úryvky staženými z internetu by se mělo zacházet jako s jakýmkoli jiným staženým obsahem - s velkou opatrností.

- Výstřižky můžete stahovat pouze z důvěryhodných webů a používat aktuální antivirový software.

- Otevřete všechny stažené soubory úryvků v poznámkovém bloku nebo v editoru XML sady Visual Studio a před instalací je pečlivě zkontrolujte. Podívejte se na následující problémy:

  - Kód fragmentu může poškodit systém, pokud jej spustíte. Před spuštěním si pozorně přečtěte zdrojový kód.

  - Blok adresy URL nápovědy souboru výstřižku může obsahovat adresy URL, které spouštějí soubor se škodlivým skriptem nebo zobrazují urážlivý web.

  - Výstřižek může obsahovat odkazy, které jsou přidány tiše do projektu a mohou být načteny z libovolného místa v systému. Tyto odkazy byly pravděpodobně staženy do počítače, ze kterého jste fragment stáhli. Fragment pak může volat metodu v odkazu, který spustí škodlivý kód. Chcete-li se před takovým útokem chránit, zkontrolujte bloky Importy a Odkazy souboru úryvku.

## <a name="see-also"></a>Viz také

- [Fragmenty kódu IntelliSense jazyka Visual Basic](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)
- [Zabezpečení aplikací](../ide/securing-applications.md)
- [Fragmenty kódu](../ide/code-snippets.md)
