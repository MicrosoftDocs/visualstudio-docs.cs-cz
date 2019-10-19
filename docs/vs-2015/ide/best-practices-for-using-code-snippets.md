---
title: Osvědčené postupy pro používání fragmentů kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets, best practices
- code snippets, security
ms.assetid: a293ec17-4dd7-4a99-8eeb-99f44a822a8b
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 74da305b69a9561573466d385c5d7b686da3693f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72620329"
---
# <a name="best-practices-for-using-code-snippets"></a>Doporučené postupy pro používání fragmentů kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kód v fragmentu kódu ukazuje pouze nejzákladnější způsob, jak něco udělat. Pro většinu aplikací je nutné kód upravit tak, aby vyhovoval aplikaci.

## <a name="handling-exceptions"></a>Zpracování výjimek
 Obvykle se vyzkouší fragment kódu... Catch blokuje a znovu vyvolá všechny výjimky. To nemusí být správná volba pro váš projekt. Pro každou výjimku existuje několik způsobů, jak reagovat. Příklady naleznete v tématu [How to: zpracovat výjimku pomocí try/catch (C# Průvodce programováním)](https://msdn.microsoft.com/library/ca8e3773-980e-4767-8633-7408540e9818) a [Try... Zachytit... Finally – příkaz](https://msdn.microsoft.com/library/d6488026-ccb3-42b8-a810-0d97b9d6472b).

## <a name="file-locations"></a>Umístění souborů
 Při přizpůsobování umístění souborů k aplikaci byste měli zvážit následující:

- Hledání přístupného umístění. Uživatelé nemusí mít přístup ke složce Program Files v počítači, takže ukládání souborů se soubory aplikace nemusí fungovat.

- Hledání zabezpečeného umístění. Ukládání souborů do kořenové složky (C: \\) není zabezpečené. Pro data aplikací doporučujeme složku \Application Data. Pro jednotlivá uživatelská data může aplikace vytvořit soubor pro každého uživatele ve složce \My Documents.

- Použijte platný název souboru. Ovládací prvky <xref:System.Windows.Forms.OpenFileDialog> a <xref:System.Windows.Forms.SaveFileDialog> můžete použít ke snížení pravděpodobnosti neplatných názvů souborů. Uvědomte si, že mezi časem, kdy uživatel vybere soubor, a časem, kdy kód zpracovává soubor, je možné soubor odstranit. Kromě toho uživatel nemusí mít oprávnění k zápisu do souboru.

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

  - Blok adresy URL pro soubor s fragmentem kódu URL může obsahovat adresy URL, které spouštějí škodlivý soubor skriptu, nebo zobrazit urážlivý webový server.

  - Fragment kódu může obsahovat odkazy, které jsou přidány tiše do projektu a mohou být načteny z libovolného místa v systému. Tyto odkazy mohou být staženy do vašeho počítače, ze kterého jste stáhli fragment kódu. Fragment kódu potom může provést volání metody v odkazu, který spustí škodlivý kód. Chcete-li chránit před takovým útokem, přečtěte si bloky import a odkazy souboru fragmentu.

## <a name="see-also"></a>Viz také
 [Visual Basicch fragmentů kódu technologie IntelliSense](https://msdn.microsoft.com/library/ffdde4c9-8141-4906-b09b-15181357a643) [zabezpečení](../ide/securing-applications.md) [fragmentů kódu](../ide/code-snippets.md) aplikací
