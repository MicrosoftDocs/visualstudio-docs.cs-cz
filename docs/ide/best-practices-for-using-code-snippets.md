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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75591707"
---
# <a name="best-practices-for-using-code-snippets"></a>Osvědčené postupy pro používání fragmentů kódu

Kód v fragmentu kódu ukazuje pouze nejzákladnější způsob, jak něco udělat. Pro většinu aplikací je nutné kód upravit tak, aby vyhovoval aplikaci.

## <a name="handling-exceptions"></a>Zpracování výjimek

Obvykle se vyzkouší fragment kódu... Catch blokuje a znovu vyvolá všechny výjimky. To nemusí být správná volba pro váš projekt. Pro každou výjimku existuje několik způsobů, jak reagovat. Příklady naleznete v tématu [How to: zpracovat výjimku pomocí try/catch (C#)](/dotnet/csharp/programming-guide/exceptions/how-to-handle-an-exception-using-try-catch) a [Try... Zachytit... Finally – příkaz (Visual Basic)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement).

## <a name="file-locations"></a>Umístění souborů

Při přizpůsobování umístění souborů k aplikaci byste měli zvážit následující:

- Hledání přístupného umístění. Uživatelé nemusí mít přístup ke složce *Program Files* v počítači, takže ukládání souborů se soubory aplikace nemusí fungovat.

- Hledání zabezpečeného umístění. Ukládání souborů do kořenové složky (*C: \\ *) není zabezpečené. Pro data aplikací doporučujeme složku *Application data* . Pro jednotlivá uživatelská data může aplikace vytvořit soubor pro každého uživatele ve složce *dokumenty* .

- Použijte platný název souboru. Pomocí <xref:System.Windows.Forms.OpenFileDialog> ovládacích prvků a můžete <xref:System.Windows.Forms.SaveFileDialog> snížit pravděpodobnost neplatných názvů souborů. Uvědomte si, že mezi časem, kdy uživatel vybere soubor, a časem, kdy kód zpracovává soubor, je možné soubor odstranit. Kromě toho uživatel nemusí mít oprávnění k zápisu do souboru.

## <a name="security"></a>Zabezpečení

Jak zabezpečený fragment závisí na tom, kde se používá ve zdrojovém kódu a jak je upraven v kódu. Následující seznam obsahuje několik oblastí, které je třeba vzít v úvahu.

- Přístup k souborům a databázím

- Zabezpečení přístupu kódu

- Ochrana prostředků (jako jsou protokoly událostí, registr)

- Ukládání tajných kódů

- Ověřování vstupů

- Předávání dat do skriptovacích technologií

Další informace najdete v tématu [zabezpečení aplikací](../ide/securing-applications.md).

## <a name="downloaded-code-snippets"></a>Stažené fragmenty kódu

Fragmenty kódu technologie IntelliSense nainstalované v rámci sady Visual Studio nejsou v bezpečí bezpečnostním rizikem. V aplikaci ale můžou vytvářet bezpečnostní rizika. Fragmenty stažené z Internetu by se měly nacházet jako s jakýmkoli jiným staženým obsahem – s mimořádnou opatrností.

- Stahovat fragmenty kódu pouze z webů, které důvěřujete, a používejte aktuální antivirový software.

- Otevřete všechny stažené soubory fragmentů v programu Poznámkový blok nebo editoru XML sady Visual Studio a pečlivě je Projděte před jejich instalací. Vyhledejte následující problémy:

  - Kód fragmentu kódu může poškodit systém, pokud jej spustíte. Před spuštěním si důkladně přečtěte zdrojový kód.

  - Blok adresy URL pro soubor s fragmentem kódu URL může obsahovat adresy URL, které spouštějí škodlivý soubor skriptu, nebo můžou zobrazit urážlivý Web.

  - Fragment kódu může obsahovat odkazy, které jsou přidány tiše do projektu a mohou být načteny z libovolného místa v systému. Tyto odkazy mohou být staženy do vašeho počítače, ze kterého jste stáhli fragment kódu. Fragment kódu potom může provést volání metody v odkazu, který spustí škodlivý kód. Chcete-li chránit před takovým útokem, přečtěte si bloky import a odkazy souboru fragmentu.

## <a name="see-also"></a>Viz také

- [Visual Basic fragmentů kódu technologie IntelliSense](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)
- [Zabezpečení aplikací](../ide/securing-applications.md)
- [Fragmenty kódu](../ide/code-snippets.md)
