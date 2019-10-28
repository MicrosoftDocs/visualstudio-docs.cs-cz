---
title: Balení a nasazení řešení služby SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- packaging [SharePoint development in Visual Studio]
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, packaging and deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 45815e03d887f4d22f2559acf741f612cab34c49
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986210"
---
# <a name="package-and-deploy-sharepoint-solutions"></a>Zabalení a nasazení řešení služby SharePoint
  Řešení služby SharePoint je obvykle nasazeno na server SharePoint pomocí souboru balíčku řešení (. wsp). Sadu Visual Studio můžete použít k uspořádání položek projektu služby SharePoint do funkcí a k vytvoření balíčku pro nasazení funkcí služby SharePoint.

 Toto téma poskytuje následující informace:

- [Vytváření funkcí a balíčků](#create-features-and-packages)

- [Podpora nástrojů pro balíčky a funkce](#feature-and-packaging-tool-support)

- [Nasazení řešení služby SharePoint](#deploy-sharepoint-solutions)

- [Nasazení souborů v řešeních služby SharePoint](#deploy-files-in-sharepoint-solutions)

## <a name="create-features-and-packages"></a>Vytváření funkcí a balíčků
 Sadu Visual Studio můžete použít k seskupení souvisejících prvků služby SharePoint do *funkce*. Například funkce pro definici seznamu kontaktů může zahrnovat instanci seznamu a definici seznamu. Tyto dva prvky můžete zkombinovat do jediné funkce pro účely nasazení. Další informace o funkcích naleznete v tématu [stavební blok: funkce](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14)).

 V dalším kroku můžete vytvořit balíček řešení služby SharePoint ( *. wsp*) a seskupit více funkcí, definic webů, sestavení a dalších souborů do jednoho balíčku, který ukládá soubory ve formátu potřebném službou SharePoint k nasazení souborů na server. Další informace najdete v tématu [stavební blok: řešení](/previous-versions/office/developer/sharepoint-2010/ee537008(v=office.14)).

## <a name="feature-and-packaging-tool-support"></a>Podpora nástrojů pro balíčky a funkce
 Nástroje pro vývoj pro SharePoint v aplikaci Visual Studio můžete použít k rychlému uspořádání souborů SharePoint do funkcí a balíčků řešení pro snazší nasazení. K nakonfigurování funkce a balíčku řešení můžete použít následující nástroje.

- Návrhář funkcí a Návrhář balíčků.

- Sbalení Průzkumníka, okno nástrojů

- Průzkumník řešení.

### <a name="feature-designer-and-package-designer"></a>Návrhář funkcí a Návrhář balíčků
 Pomocí návrháře funkcí můžete vytvořit funkce, nastavit obory a označit jiné funkce jako závislosti. Návrhář také zobrazí konečný soubor XML, který popisuje jednotlivé funkce. Další informace najdete v tématu [Vytvoření funkcí služby SharePoint](../sharepoint/creating-sharepoint-features.md).

 Použijte funkci na konkrétní web nebo skupinu webů nastavením jejího *oboru* v Návrháři funkcí. Pokud je funkce aktivována pro jednotlivý web, funkce funguje pouze na daném webu. Je-li funkce pro kolekci webů aktivována, položky v této funkci se vztahují na celou kolekci webů. Další informace naleznete v tématu [Scope elementu](/previous-versions/office/developer/sharepoint-2010/ms476615(v=office.14)).

 Pokud vaše funkce spoléhá na jiné funkce, můžete nastavit *závislost aktivace funkcí* k označení závislých funkcí před zpřístupněním vaší funkce. Závislost aktivace funkce kontroluje, zda jsou závislé funkce již v daném oboru aktivovány. Další informace najdete v tématu [závislosti a rozsah aktivace](/previous-versions/office/developer/sharepoint-2010/aa543162(v=office.14)).

 V Návrháři balíčků můžete prvky služby SharePoint seskupit do jednoho balíčku řešení a nakonfigurovat, zda má být během nasazení obnoven webový server. Chcete-li nastavit typ serveru nasazení, použijte okno **vlastnosti** . Návrhář také generuje soubor XML, který popisuje obsah balíčku. Další informace najdete v tématu [vytváření balíčků řešení služby SharePoint](../sharepoint/creating-sharepoint-solution-packages.md).

 Během nasazování se služba Internetová informační služba (IIS) zastavila, aby zkopírovala soubory řešení na server SharePoint. Pomocí návrháře balíčků v aplikaci Visual Studio můžete vybrat, zda má být webový server restartován. Chcete-li nakonfigurovat, zda je řešení nasazeno na předřazený webový server nebo na aplikační server, použijte okno **vlastnosti** . Další informace naleznete v tématu [element Solution (řešení)](/previous-versions/office/developer/sharepoint-2010/ms412929(v=office.14)).

### <a name="packaging-explorer"></a>Průzkumník balení
 Chcete-li doplnit návrháře funkcí a návrháře balíčků, můžete pomocí Průzkumníka balíčků seskupit své soubory služby SharePoint do funkcí a balíčků. Kromě toho můžete zobrazit hierarchické zobrazení balíčku, funkce, položky projektu služby SharePoint a soubory. Průzkumník balíčků je okno nástroje, které můžete použít k dokončení následujících úloh:

- Otevřete položky a soubory projektu služby SharePoint.

- Přetáhněte položky SharePointového projektu z jedné funkce na jinou.

- Přetáhněte položky a funkce projektu služby SharePoint z jednoho balíčku do jiného.

- Přidejte do balíčku novou funkci.

- Otevřete funkci nebo Návrhář balíčku.

- Ověřte funkce a balíčky.

  Nástroje pro vývoj pro SharePoint v aplikaci Visual Studio obsahují pravidla ověřování, která vám pomůžou zajistit, že balíček řešení je správně vytvořený. Kromě toho pravidla ověřují, jestli se soubor řešení *WSP* dá úspěšně nasadit a aktivovat na sharepointovém serveru. Další informace o schématu XML pro funkce naleznete v tématu [schémata funkcí](/previous-versions/office/developer/sharepoint-2010/ms414322(v=office.14)).

  Můžete přidat vlastní funkce a pravidla pro ověření balíčku do systému projektu služby SharePoint. Další informace najdete v tématu [Postupy: vytváření vlastních funkcí a pravidel ověřování balíčku pro řešení služby SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

  Další informace o Průzkumníkovi balíčků naleznete v tématu [How to: Add and Remove Features and Items to a Remove-Package to using the balící Explorer](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).

### <a name="solution-explorer"></a>Průzkumník řešení
 Můžete použít Průzkumník řešení k procházení a otevírání souborů projektu služby SharePoint. Pomocí místní nabídky v Průzkumník řešení můžete přidat funkce, přijímače událostí funkcí a prostředky funkcí. Kromě toho můžete otevřít návrháře funkcí a návrháře balíčků a nakonfigurovat tak funkce a balíčky pro nasazení.

## <a name="deploy-sharepoint-solutions"></a>Nasazení řešení služby SharePoint
 Po přizpůsobení funkcí a balíčku v aplikaci Visual Studio můžete vytvořit soubor *. wsp* pro nasazení na servery SharePoint. Můžete použít Visual Studio k ladění a testování. *WSP* pouze na serveru SharePoint ve vývojovém počítači. Další informace o tom, jak nasadit řešení služby SharePoint na vzdálený server SharePoint, naleznete v tématu [nasazení řešení](/previous-versions/office/developer/sharepoint-2010/aa544500(v=office.14)).

 Můžete také přizpůsobit kroky nasazení na vývojovém počítači. Další informace najdete v tématu [nasazení, publikování a Upgrade balíčků řešení služby SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).

## <a name="deploy-files-in-sharepoint-solutions"></a>Nasazení souborů v řešeních služby SharePoint
 Obvykle když přidáte položku SharePointového projektu do řešení služby SharePoint, jsou zahrnuty všechny požadované soubory. Soubory, které mohou být kompilovány (soubory kódu), jsou integrovány do výstupního sestavení řešení. Můžete ale také přidat soubory, které nejsou kompilovatelný, například *. XML*, *. txt*nebo soubory prostředků, do projektu služby SharePoint. Tyto soubory nejsou automaticky zabaleny do vašeho řešení. Chcete-li zajistit, že jsou zabaleny, buď přidejte soubory do mapované složky nebo do položky projektu služby SharePoint.

 Soubory přidané do mapovaných složek se při nasazení řešení automaticky zkopírují do podregistru služby SharePoint. Soubory přidané do položky projektu služby SharePoint jsou nasazeny do umístění, které je zadáno ve vlastnosti **umístění nasazení** pro každý soubor, který je částečně nastaven na základě vlastnosti **typ nasazení** . Ve výchozím nastavení je hodnota vlastnosti **typ nasazení** nastaveno na **Nenasazení**, což znamená, že soubor není nasazen s řešením. Je nutné nastavit další hodnotu vlastnosti tak, aby obsahovala soubor v balíčku.

 Chcete-li například přidat soubor *. XML* do projektu služby SharePoint, proveďte jednu z následujících akcí:

- Přidejte do projektu mapovanou složku SharePointu rozložení. Tím se vytvoří **Průzkumník řešení** složka s názvem **Layouts** , která má podsložku pro projekt. Přidejte soubor *. XML* do nové podsložky. Ve výchozím nastavení je soubor nasazen do systému souborů služby SharePoint v části *.. \TEMPLATE\LAYOUTS\\název složky\<* . Informace o tom, jak přidat mapované složky, naleznete v tématu [How to: Add and Remove mapované složky](../sharepoint/how-to-add-and-remove-mapped-folders.md).

- Přidejte soubor *. XML* do složky položky projektu služby SharePoint a poté změňte vlastnost **typ nasazení** souboru *. XML* z **nasazení** na jiné nastavení, jako je například **RootFile** nebo **ElementFile**. Odpovídající nastavení **typu nasazení** závisí na souboru a projektu. Další informace o nastavení vlastností **typu nasazení** najdete v tématu [vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md).

  Pokud se přidaný soubor nevztahuje na žádný konkrétní projekt v řešení, můžete do řešení přidat prázdný projekt služby SharePoint a následně do něj přidat další soubory. Další alternativou pro nasazení souborů do služby SharePoint, zejména databáze obsahu, je přidání modulu do projektu a přidání souborů do modulu. Další informace najdete v tématu [použití modulů k zahrnutí souborů v řešení](../sharepoint/using-modules-to-include-files-in-the-solution.md).

## <a name="see-also"></a>Viz také:
- [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Sestavování a ladění řešení služby SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
