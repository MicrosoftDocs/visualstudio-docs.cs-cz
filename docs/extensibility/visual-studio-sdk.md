---
title: Sada Visual Studio SDK | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56f772d7d27f11318cdeb0bf365373d5f7c1294b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698080"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
Sada Visual Studio SDK pomáhá rozšířit funkce sady Visual Studio nebo integrovat nové funkce do sady Visual Studio. Rozšíření můžete distribuovat ostatním uživatelům a také webu Visual Studio Marketplace. Následují některé způsoby, kterými můžete rozšířit Visual Studio:

- Přidání příkazů, tlačítek, nabídek a dalších prvků uživatelského rozhraní do rozhraní IDE

- Přidání oken nástrojů pro nové funkce

- Rozšíření technologie IntelliSense pro daný jazyk nebo poskytnutí technologie IntelliSense pro nové programovací jazyky

- Pomocí žárovek můžete poskytnout rady a návrhy, které vývojářům pomohou napsat lepší kód

- Povolení podpory pro nový jazyk

- Přidání vlastního typu projektu

- Oslovte miliony vývojářů prostřednictvím webu Visual Studio Marketplace

  Pokud jste rozšíření sady Visual Studio nikdy předtím nenapsali, měli byste najít další informace o těchto funkcích a na [začátku vývoje rozšíření sady Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).

## <a name="install-the-visual-studio-sdk"></a>Instalace sady Visual Studio SDK
 Sada Visual Studio SDK je volitelná funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="whats-new-in-the-visual-studio-2017-sdk"></a>Co je nového v sadě Visual Studio 2017 SDK
 Sada Visual Studio SDK obsahuje některé nové funkce, jako je například formát VSIX v3, stejně jako narušující změny, které mohou vyžadovat aktualizaci rozšíření. Další informace naleznete [v tématu Co je nového v sadě Visual Studio 2017 SDK](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md).

## <a name="visual-studio-user-experience-guidelines"></a>Pokyny pro uživatelské prostředí sady Visual Studio
 Získejte skvělé tipy pro návrh uživatelského rozhraní pro vaše rozšíření v [pokynech pro uživatelské prostředí sady Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

 Můžete se také dozvědět, jak vaše rozšíření vypadat skvěle na zařízeních s vysokým DPI s [adresou DPI problémy](../extensibility/addressing-dpi-issues2.md) článku.

 Využijte [službu Image service a catalog](../extensibility/image-service-and-catalog.md) pro skvělou správu obrázků a podporu pro vysoké DPI a tématy.

## <a name="find-and-install-existing-visual-studio-extensions"></a>Vyhledání a instalace existujících rozšíření sady Visual Studio
 Rozšíření sady Visual Studio najdete v dialogovém **okně Rozšíření a aktualizace** v nabídce **Nástroje.** Další informace naleznete v [tématu Hledání a použití rozšíření sady Visual Studio](../ide/finding-and-using-visual-studio-extensions.md). Rozšíření najdete také na [webu Visual Studio Marketplace.](https://marketplace.visualstudio.com/)

## <a name="visual-studio-sdk-reference"></a>Odkaz na sdk sady Visual Studio
 Odkaz na rozhraní API sady Visual Studio SDK najdete v [referenční příručce sady Visual Studio SDK .](../extensibility/visual-studio-sdk-reference.md)

## <a name="visual-studio-sdk-samples"></a>Ukázky sady Visual Studio SDK
 Open source příklady rozšíření VS SDK najdete na GitHubu na [ukázkách Visual Studia](https://github.com/Microsoft/VSSDK-Extensibility-Samples). Toto úložiště GitHub obsahuje ukázky, které ilustrují různé rozšiřitelné funkce v sadě Visual Studio.

## <a name="other-visual-studio-sdk-resources"></a>Další prostředky sady Visual Studio SDK
 Pokud máte dotazy týkající se sady VSSDK nebo se chcete podělit o své zkušenosti s vývojem rozšíření, můžete použít [Fórum rozšiřitelnosti sady Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) nebo [chatovací místnost ExtendVS Gitter](https://gitter.im/Microsoft/extendvs).

 Další informace naleznete v [blogu VSX Arcana](https://blogs.msdn.microsoft.com/vsx/) a v řadě blogů napsaných mvpy Microsoft:

- [Oblíbená rozšíření sady Visual Studio](https://scottdorman.blog/2014/10/05/favorite-visual-studio-extensions/)

- [Rozšiřitelnost sady Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)

- [Rozšíření sady Visual Studio](https://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)

## <a name="see-also"></a>Viz také

- [Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md)
- [Postup: Migrace projektů rozšiřitelnosti do Visual Studia 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)
- [Časté dotazy: Převod doplňků na rozšíření VSPackage](/visualstudio/extensibility/faq-converting-add-ins-to-vspackage-extensions?view=vs-2015)
- [Správa více vláken ve spravovaném kódu](../extensibility/managing-multiple-threads-in-managed-code.md)
- [Rozšíření nabídek a příkazů](../extensibility/extending-menus-and-commands.md)
- [Přidání příkazů na panely nástrojů](../extensibility/adding-commands-to-toolbars.md)
- [Rozšíření a přizpůsobení oken nástrojů](../extensibility/extending-and-customizing-tool-windows.md)
- [Rozšíření editoru a jazykových služeb](../extensibility/editor-and-language-service-extensions.md)
- [Rozšířit projekty](../extensibility/extending-projects.md)
- [Rozšíření uživatelských nastavení a možností](../extensibility/extending-user-settings-and-options.md)
- [Vytvoření vlastních šablon projektů a položek](../extensibility/creating-custom-project-and-item-templates.md)
- [Rozšířit vlastnosti a okno vlastnosti](../extensibility/extending-properties-and-the-property-window.md)
- [Rozšíření dalších částí sady Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Využívání a poskytování služeb](../extensibility/using-and-providing-services.md)
- [Správa balíčků VSPackage](../extensibility/managing-vspackages.md)
- [Izolované prostředí sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
- [Rozšíření aplikace Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
- [Práce se sadou Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)
- [Podpora sady Visual Studio SDK](../extensibility/support-for-the-visual-studio-sdk.md)
- [Odkaz na sdk sady Visual Studio](../extensibility/visual-studio-sdk-reference.md)
