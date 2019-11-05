---
title: Sada Visual Studio SDK | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 73c14c61702ec978d8ffec896b13204c238762a2
ms.sourcegitcommit: 97623fd6190c43fed0d2ee7af92b01c375282622
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/04/2019
ms.locfileid: "73568807"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
Sada Visual Studio SDK vám pomůže s rozšiřováním funkcí sady Visual Studio nebo integrací nových funkcí do sady Visual Studio. Rozšíření můžete distribuovat dalším uživatelům i Visual Studio Marketplace. Níže jsou uvedeny některé způsoby, jak můžete sadu Visual Studio rozšíří:

- Přidání příkazů, tlačítek, nabídek a dalších prvků uživatelského rozhraní do integrovaného vývojového prostředí

- Přidat okna nástrojů pro nové funkce

- Rozšiřování technologie IntelliSense pro daný jazyk nebo poskytnutí IntelliSense pro nové programovací jazyky

- Používejte žárovky k poskytování pomocných rad a návrhů, které vývojářům pomůžou psát lepší kód.

- Povolit podporu pro nový jazyk

- Přidat vlastní typ projektu

- Oslovení milionů vývojářů prostřednictvím Visual Studio Marketplace

  Pokud jste ještě nikdy nezapsali rozšíření sady Visual Studio, měli byste najít další informace o těchto funkcích a [začít vyvíjet rozšíření sady Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).

## <a name="install-the-visual-studio-sdk"></a>Instalace sady Visual Studio SDK
 Sada Visual Studio SDK je volitelnou funkcí instalačního programu sady Visual Studio. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="whats-new-in-the-visual-studio-2017-sdk"></a>Co je nového v sadě Visual Studio 2017 SDK
 Sada Visual Studio SDK obsahuje některé nové funkce, jako je například formát VSIX v3, a také zásadní změny, které mohou vyžadovat aktualizaci rozšíření. Další informace najdete v tématu [co je nového v sadě Visual Studio 2017 SDK](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md).

## <a name="visual-studio-user-experience-guidelines"></a>Pokyny pro uživatelské prostředí sady Visual Studio
 V [pokynech pro uživatelské prostředí sady Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)získáte Skvělé tipy pro návrh uživatelského rozhraní pro vaše rozšíření.

 Můžete se také seznámit s tím, jak se má vaše rozšíření na zařízeních s vysokým rozlišením DPI zobrazovat v článku s [problémy s adresou dpi](../extensibility/addressing-dpi-issues2.md) .

 Využijte výhod [služby image a katalogu](../extensibility/image-service-and-catalog.md) pro skvělou správu imagí a podporu vysokého rozlišení DPI.

## <a name="find-and-install-existing-visual-studio-extensions"></a>Vyhledat a nainstalovat existující rozšíření sady Visual Studio
 Rozšíření sady Visual Studio najdete v dialogovém okně **rozšíření a aktualizace** v nabídce **nástroje** . Další informace najdete v tématu [hledání a používání rozšíření sady Visual Studio](../ide/finding-and-using-visual-studio-extensions.md). V [Visual Studio Marketplace](https://marketplace.visualstudio.com/) můžete také najít rozšíření.

## <a name="visual-studio-sdk-reference"></a>Referenční informace k sadě Visual Studio SDK
 Referenční informace k rozhraní API sady Visual Studio SDK najdete v [referenčních informacích k sadě Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md).

## <a name="visual-studio-sdk-samples"></a>Ukázky sady Visual Studio SDK
 Příklady open source rozšíření sady VS SDK najdete na webu GitHub v sadě [Visual Studio Samples](https://aka.ms/vs2015sdksamples). Toto úložiště GitHub obsahuje ukázky, které ilustrují různé rozšiřitelné funkce v aplikaci Visual Studio.

## <a name="other-visual-studio-sdk-resources"></a>Další prostředky sady Visual Studio SDK
 Pokud máte dotazy týkající se VSSDK nebo chcete sdílet své zkušenosti s vývojem rozšíření, můžete použít [Fórum rozšiřitelnosti sady Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) nebo [extendvs gitteru chatroom](https://gitter.im/Microsoft/extendvs).

 Další informace najdete na [blogu VSX Arcana](https://blogs.msdn.microsoft.com/vsx/) a v několika blogůch zapsaných přes Microsoft MVP:

- [Oblíbená rozšíření sady Visual Studio](https://scottdorman.blog/2014/10/05/favorite-visual-studio-extensions/)

- [Rozšiřitelnost sady Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)

- [Rozšíření sady Visual Studio](https://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)

## <a name="see-also"></a>Viz také:

- [Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md)
- [Postupy: migrace rozšiřujících projektů do sady Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)
- [Nejčastější dotazy: převod doplňků na rozšíření VSPackage](/visualstudio/extensibility/faq-converting-add-ins-to-vspackage-extensions?view=vs-2015)
- [Správa více vláken ve spravovaném kódu](../extensibility/managing-multiple-threads-in-managed-code.md)
- [Rozšiřování nabídek a příkazů](../extensibility/extending-menus-and-commands.md)
- [Přidat příkazy na panely nástrojů](../extensibility/adding-commands-to-toolbars.md)
- [Rozšiřování a přizpůsobení oken nástrojů](../extensibility/extending-and-customizing-tool-windows.md)
- [Editor a rozšíření služby jazyka](../extensibility/editor-and-language-service-extensions.md)
- [Roztažení projektů](../extensibility/extending-projects.md)
- [Rozšíří uživatelská nastavení a možnosti.](../extensibility/extending-user-settings-and-options.md)
- [Vytváření vlastních šablon projektů a položek](../extensibility/creating-custom-project-and-item-templates.md)
- [Rozšířené vlastnosti a okno vlastností](../extensibility/extending-properties-and-the-property-window.md)
- [Rozšiřování dalších částí sady Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Používání a poskytování služeb](../extensibility/using-and-providing-services.md)
- [Spravovat VSPackage](../extensibility/managing-vspackages.md)
- [Izolované prostředí sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
- [Dodávat rozšíření sady Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
- [Práce se sadou Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)
- [Podpora sady Visual Studio SDK](../extensibility/support-for-the-visual-studio-sdk.md)
- [Referenční informace k sadě Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md)
