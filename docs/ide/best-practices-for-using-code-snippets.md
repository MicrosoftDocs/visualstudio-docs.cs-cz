---
title: Doporučené postupy pro používání fragmentů kódu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets, best practices
- code snippets, security
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b8c7a04f2a2fb2ef59a41953c82da4254f213084
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2018
ms.locfileid: "39179528"
---
# <a name="best-practices-for-using-code-snippets"></a>Osvědčené postupy pro používání fragmentů kódu

Kód ve fragmentu kódu zobrazuje pouze základní způsob, jak něco udělat. Pro většinu aplikací musí změnit kód tak, aby odpovídala aplikace.

## <a name="handling-exceptions"></a>Zpracování výjimek

Obvykle fragment kódu Try... Bloky catch zachycují a znovu vyvolat všechny výjimky. Který nemusí být správnou volbou pro váš projekt. Pro každou výjimku existuje několik způsobů, jak reagovat. Příklady najdete v tématu [postupy: zpracování výjimky pomocí bloku try/catch (C#)](/dotnet/csharp/programming-guide/exceptions/how-to-handle-an-exception-using-try-catch) a [zkuste... Catch... Finally – příkaz (Visual Basic)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement).

## <a name="file-locations"></a>Umístění souborů

Při umístění souborů můžete přizpůsobit pro vaši aplikaci, byste uvažovat o následujícím:

- Hledání na dostupném místě. Nemusí mít uživatelé přístup k *Program Files* složky na počítači, takže ukládání souborů pomocí aplikace soubory května není pracovní.

- Hledání na bezpečném místě. Ukládání souborů v kořenové složce (*C:\\*) není zabezpečený. Pro data aplikací, doporučujeme, abyste *Data aplikací* složky. Pro data jednotlivých uživatelů, můžete vytvořit aplikace pro každého uživatele v souboru *dokumenty* složky.

- Pomocí platný název souboru. Můžete použít <xref:System.Windows.Forms.OpenFileDialog> a <xref:System.Windows.Forms.SaveFileDialog> ovládacích prvků pro snížení pravděpodobnosti výskytu neplatné názvy souborů. Mějte na paměti, že mezi časem uživatel vybere soubor a čas, váš kód zpracovává soubor, mohou odstranit soubor. Kromě toho uživatel nemá oprávnění k zápisu do souboru.

## <a name="security"></a>Zabezpečení

Zabezpečené fragment je závisí na jeho použití ve zdrojovém kódu a jak je změnit, až bude v kódu. Následující seznam obsahuje několik oblastí, které musíte vzít v úvahu.

- Přístup k souboru a databáze

- Zabezpečení přístupu kódu

- Ochrana prostředků (jako jsou protokoly událostí, registr)

- Ukládání tajných klíčů

- Ověřuje se, jestli vstupy

- Předávání dat skriptovací technologie

Další informace najdete v tématu [zabezpečení aplikací](../ide/securing-applications.md).

## <a name="downloaded-code-snippets"></a>Fragmenty kódu stažené

Fragmenty kódu technologie IntelliSense ve Visual Studio nainstalované nejsou v samotných ohrožení zabezpečení. Může ale vytvořit bezpečnostní rizika ve vaší aplikaci. Fragmenty kódu stažené z Internetu měli zacházet jako s další obsah stažený – s nejvyšší opatrností.

- Stáhnout fragmenty pouze z lokality, které důvěřujete a použít aktuální antivirový software.

- Otevřít všechny soubory stažené fragmentu kódu v programu Poznámkový blok nebo editoru XML sady Visual Studio a pečlivě zkontrolujte před instalací. Vyhledejte následující problémy:

    - Fragment kódu by mohl poškodit váš systém, pokud je spuštěn. Pečlivě si přečtěte zdrojový kód před jejím spuštěním.

    - Adresa URL nápovědy bloku soubor výstřižku může obsahovat adresy URL, které spustit škodlivý soubor nebo zobrazit urážlivé webu.

    - Fragment kódu mohou obsahovat odkazy, které jsou tiše přidány do projektu a mohou být načteny z kdekoli ve vašem systému. Tyto odkazy může být stažené do vašeho počítače ze kterého jste stáhli fragmentu kódu. Fragment kódu může proveďte volání metody v odkazu, který se spustí škodlivý kód. Chránit proti takového útoku, najdete v tématu importy a odkazy na bloky souboru fragmentu kódu.

## <a name="see-also"></a>Viz také:

- [Fragmenty kódu technologie IntelliSense jazyka Visual Basic](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)
- [Zabezpečení aplikací](../ide/securing-applications.md)
- [Fragmenty kódu](../ide/code-snippets.md)