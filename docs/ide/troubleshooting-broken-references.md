---
title: Řešení problémů s poškozenými odkazy
description: Naučte se řešit potíže s přerušenými odkazy, které mohou být způsobeny jinou výjimkou vašich aplikací, které neumožňují najít odkazovanou součást.
ms.custom: SEO-VS-2020
ms.date: 03/21/2017
ms.topic: troubleshooting
helpviewer_keywords:
- C# projects, references
- Visual Basic projects, references
- troubleshooting references
- referencing files from projects
- referencing components, troubleshooting
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 627724410ac9e0829faeb23cb5b0eef01b153293
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479170"
---
# <a name="troubleshoot-broken-references"></a>Řešení problémů s poškozenými odkazy

Pokud se vaše aplikace pokusí použít poškozený odkaz, je vygenerována chyba výjimky. Neschopnost najít odkazovanou komponentu je primární Trigger pro chybu, ale existuje několik situací, ve kterých může být odkaz považován za poškozený. Tyto instance jsou uvedené v následujícím seznamu:

- Odkazovaná cesta k projektu je nesprávná nebo neúplná.

- Odkazovaný soubor byl odstraněn.

- Odkazovaný soubor byl přejmenován.

- Připojení k síti nebo ověřování se nezdařilo.

- Odkaz je na komponentu modelu COM, která není v počítači nainstalována.

Níže jsou uvedená opatření pro tyto problémy.

> [!NOTE]
> Soubory v sestaveních jsou odkazovány pomocí absolutních cest v souboru projektu. Proto je možné, že uživatelé, kteří pracují ve více vývojářích prostředí, mají v místním prostředí chybějící odkazované sestavení. Aby nedocházelo k těmto chybám, je lepší v těchto případech přidat odkazy z projektu na projekt. Další informace naleznete v tématu [programování se sestaveními](/dotnet/framework/app-domains/programming-with-assemblies).

## <a name="reference-path-is-incorrect"></a>Cesta odkazu není správná.

Pokud jsou projekty sdíleny v různých počítačích, některé odkazy nemusí být nalezeny, pokud je komponenta umístěna v jiném adresáři v každém počítači. Odkazy jsou uloženy pod názvem souboru komponenty (například *MyComponent*). Při přidání odkazu do projektu je umístění složky souboru komponenty (například *C:\MyComponents*) připojeno k vlastnosti projektu **ReferencePath** .

Po otevření projektu se pokusí vyhledat tyto soubory odkazované součásti hledáním v adresářích v cestě reference. Pokud je projekt otevřen v počítači, který ukládá komponentu do jiného adresáře, například *D:\MyComponents*, odkaz nebyl nalezen a v **seznam úkolů** se zobrazí chyba.

Chcete-li tento problém vyřešit, můžete poškozený odkaz odstranit a pak ho nahradit pomocí dialogového okna **Přidat odkaz** . Dalším řešením je použít položku **referenční cesty** na stránkách vlastností projektu a upravit složky v seznamu tak, aby odkazovaly na správná umístění. Vlastnost **cesty odkazů** je u každého uživatele na každém počítači trvalá. Proto změna referenční cesty nemá vliv na ostatní uživatele projektu.

> [!TIP]
> Odkazy z projektu na projekt nemají tyto problémy. Z tohoto důvodu použijte místo odkazů na soubory, pokud je to možné.

### <a name="to-fix-a-broken-project-reference-by-correcting-the-reference-path"></a>Oprava poškozeného odkazu na projekt opravou cesty reference

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na uzel projektu a klikněte na příkaz **vlastnosti**.

   Zobrazí se **Návrhář projektu** .

1. Pokud používáte Visual Basic, vyberte stránku **odkazy** a klikněte na tlačítko odkazy na **cesty** . V dialogovém okně **cesty k odkazům** zadejte cestu ke složce, která obsahuje položku, na kterou chcete odkazovat, v poli **Složka** a pak klikněte na tlačítko **Přidat složku** .

    Pokud používáte jazyk C#, vyberte stránku **cesty odkazů** . Do pole **Složka** zadejte cestu ke složce obsahující položku, na kterou chcete odkazovat, a poté klikněte na tlačítko **Přidat složku** .

## <a name="referenced-file-has-been-deleted"></a>Odkazovaný soubor byl odstraněn.

Je možné, že se soubor, na který se odkazuje, odstranil a na jednotce už neexistuje.

### <a name="to-fix-a-broken-project-reference-for-a-file-that-no-longer-exists-on-your-drive"></a>Oprava poškozeného odkazu na projekt pro soubor, který již na jednotce neexistuje

- Odstraňte odkaz.

- Pokud odkaz existuje v jiném umístění v počítači, přečtěte si ho z tohoto umístění.

## <a name="referenced-file-has-been-renamed"></a>Odkazovaný soubor byl přejmenován.

Je možné, že odkazovaný soubor byl přejmenován.

### <a name="to-fix-a-broken-reference-for-a-file-that-has-been-renamed"></a>Oprava poškozeného odkazu na soubor, který byl přejmenován

- Odstraňte odkaz a pak přidejte odkaz na přejmenovaný soubor.

- Pokud odkaz existuje v jiném umístění v počítači, budete ho muset číst z tohoto umístění.

## <a name="network-connection-or-authentication-has-failed"></a>Připojení k síti nebo ověřování se nezdařilo.

Může existovat celá řada možných příčin nepřístupných souborů: chybné síťové připojení nebo neúspěšné ověření, například. Každá příčina může mít jedinečný způsob obnovení; Například může být nutné požádat o přístup k požadovaným prostředkům místního správce. Odstranění odkazu a oprava kódu, který ho použil, je vždycky možnost.

## <a name="com-component-is-not-installed-on-computer"></a>Součást COM není v počítači nainstalována.

Pokud uživatel přidal odkaz na komponentu COM a druhý uživatel se pokusí spustit kód v počítači, na kterém není tato součást nainstalována, obdrží druhý uživatel chybu, že odkaz je přerušen. Při instalaci komponenty na druhý počítač se chyba opraví. Další informace o tom, jak používat odkazy na komponenty modelu COM v projektech, naleznete v tématu [interoperabilita modelu COM v .NET Frameworkch aplikacích](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications).

## <a name="see-also"></a>Viz také

- [Stránka Odkazy, návrhář projektu (Visual Basic)](../ide/reference/references-page-project-designer-visual-basic.md)
