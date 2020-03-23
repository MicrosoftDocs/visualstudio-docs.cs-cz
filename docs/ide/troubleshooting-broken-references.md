---
title: Řešení problémů s poškozenými odkazy
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
ms.openlocfilehash: a5116d2487ca9f53c460e1cae8f362f3ff1bcdf8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565913"
---
# <a name="troubleshoot-broken-references"></a>Řešení problémů s poškozenými odkazy

Pokud se aplikace pokusí použít nefunkční odkaz, je generována chyba výjimky. Neschopnost najít odkazované komponenty je primární aktivační událost pro chybu, ale existuje několik situací, ve kterých odkaz lze považovat za přerušené. Tyto instance jsou zobrazeny v následujícím seznamu:

- Referenční cesta projektu je nesprávná nebo neúplná.

- Odkazovaný soubor byl odstraněn.

- Odkazovaný soubor byl přejmenován.

- Síťové připojení nebo ověřování se nezdařilo.

- Odkaz je na součást modelu COM, která není v počítači nainstalována.

Níže jsou uvedeny opravné prostředky k těmto problémům.

> [!NOTE]
> Soubory v sestaveních jsou odkazovány s absolutní cesty v souboru projektu. Proto je možné, že uživatelé, kteří pracují v prostředí s více vývojáři, budou v místním prostředí chybět odkazované sestavení. Chcete-li se vyhnout těmto chybám, je lepší v těchto případech přidat odkazy projektu na projekt. Další informace naleznete [v tématu Programování se sestavami](/dotnet/framework/app-domains/programming-with-assemblies).

## <a name="reference-path-is-incorrect"></a>Referenční cesta je nesprávná.

Pokud jsou projekty sdíleny v různých počítačích, některé odkazy nemusí být nalezeny, pokud je součást umístěna v jiném adresáři v každém počítači. Odkazy jsou uloženy pod názvem souboru komponenty (například *MyComponent).* Při přidání odkazu do projektu je k vlastnosti projektu **ReferencePath** připojeno umístění složky souboru komponenty (například *C:\MyComponents).*

Při otevření projektu se pokusí vyhledat tyto odkazované soubory součástí vyhledáním v adresářích na referenční cestě. Pokud je projekt otevřen v počítači, ve který je komponenta uložena v jiném adresáři, například *D:\MyComponents*, nelze odkaz najít a v **seznamu úkolů**se zobrazí chyba .

Chcete-li tento problém vyřešit, můžete poškozený odkaz odstranit a nahradit jej pomocí dialogového okna **Přidat odkaz.** Jiné řešení je použít položku **Referenční cesta** na stránkách vlastností projektu a upravit složky v seznamu tak, aby odkazovaly na správná umístění. **Vlastnost Reference Path** je zachována pro každého uživatele v každém počítači. Proto úprava referenční cesty nemá vliv na ostatní uživatele projektu.

> [!TIP]
> Odkazy na projekt na projekt nemají tyto problémy. Z tohoto důvodu je použijte místo odkazů na soubory, pokud je to možné.

### <a name="to-fix-a-broken-project-reference-by-correcting-the-reference-path"></a>Oprava poškozeného odkazu na projekt opravou referenční cesty

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel projektu a klepněte na příkaz **Vlastnosti**.

   Zobrazí se **Návrhář projektu.**

1. Pokud používáte jazyk Visual Basic, vyberte stránku **Odkazy** a klepněte na tlačítko **Referenční cesty.** V dialogovém okně **Referenční cesty** zadejte cestu ke složce obsahující položku, na kterou chcete odkazovat, do pole **Složka** a klepněte na tlačítko **Přidat složku.**

    Pokud používáte C#, vyberte stránku **Referenční cesty.** Do pole **Složka** zadejte cestu ke složce obsahující položku, na kterou chcete odkazovat, a klikněte na tlačítko **Přidat složku.**

## <a name="referenced-file-has-been-deleted"></a>Odkazovaný soubor byl odstraněn.

Je možné, že odkazovaný soubor byl odstraněn a na jednotce již neexistuje.

### <a name="to-fix-a-broken-project-reference-for-a-file-that-no-longer-exists-on-your-drive"></a>Oprava poškozeného odkazu na projekt pro soubor, který na jednotce již neexistuje

- Odstraňte odkaz.

- Pokud odkaz existuje v jiném umístění v počítači, přečtěte si jej z tohoto umístění.

## <a name="referenced-file-has-been-renamed"></a>Odkazovaný soubor byl přejmenován.

Je možné, že odkazovaný soubor byl přejmenován.

### <a name="to-fix-a-broken-reference-for-a-file-that-has-been-renamed"></a>Oprava poškozeného odkazu na soubor, který byl přejmenován

- Odstraňte odkaz a přidejte odkaz na přejmenovaný soubor.

- Pokud odkaz existuje v jiném umístění v počítači, je nutné jej přečíst z tohoto umístění.

## <a name="network-connection-or-authentication-has-failed"></a>Síťové připojení nebo ověřování se nezdařilo.

Může existovat mnoho možných příčin nepřístupných souborů: například neúspěšné síťové připojení nebo neúspěšné ověřování. Každá příčina může mít jedinečný prostředek k zotavení; Například budete muset kontaktovat místního správce pro přístup k požadovaným prostředkům. Odstranění odkazu a oprava kódu, který jej používal, je však vždy možností.

## <a name="com-component-is-not-installed-on-computer"></a>Součást MODELU COM není v počítači nainstalována.

Pokud uživatel přidal odkaz na komponentu modelu COM a druhý uživatel se pokusí spustit kód v počítači, ve který není nainstalována tato součást, zobrazí se druhému uživateli chyba, že odkaz je přerušen. Instalace součásti do druhého počítače chybu opraví. Další informace o použití odkazů na součásti modelu COM v projektech naleznete v [tématu Interoperabilita modelu COM v aplikacích rozhraní .NET Framework](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications).

## <a name="see-also"></a>Viz také

- [Stránka Odkazy, návrhář projektu (Visual Basic)](../ide/reference/references-page-project-designer-visual-basic.md)
