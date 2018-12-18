---
title: Zabalení a nasazení řešení služby SharePoint | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- packaging [SharePoint development in Visual Studio]
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, packaging and deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6c5993f09581faf6e3cedb4c71598ea26b16b699
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863266"
---
# <a name="package-and-deploy-sharepoint-solutions"></a>Zabalení a nasazení řešení služby SharePoint
  Obvykle nasazuje řešení služby SharePoint na SharePoint server s použitím souboru balíčku (.wsp) řešení. Visual Studio můžete použít k uspořádání položek projektu služby SharePoint do funkcí a chcete-li vytvořit balíček pro nasazení vašich funkcí služby SharePoint.  
  
 Toto téma poskytuje následující informace:  
  
-   [Vytváření funkcí a balíčků](#Creating)  
  
-   [Funkce a podpora nástroje balení](#Tools)  
  
-   [Nasazení řešení služby SharePoint](#Deploying)  
  
-   [Nasazení souborů v řešení služby SharePoint](#DeployingFiles)  
  
## <a name="create-features-and-packages"></a>Vytváření funkcí a balíčků
 Visual Studio můžete použít k seskupení souvisejících prvků SharePoint do *funkce*. Funkce pro definici seznamu kontaktů mohou být například instanci seznamu a definice seznamu. Tyto dva prvky můžete zkombinovat do jedné funkce pro účely nasazení. Další informace o funkcích najdete v tématu [stavebním blokem: funkce](http://go.microsoft.com/fwlink/?LinkID=169183).  
  
 V dalším kroku vytvoříte balíčku řešení služby SharePoint (*.wsp*) můžete seskupit několik funkcí, lokality definice sestavení a dalších souborů do jediného balíčku, který ukládá soubory ve formátu vyžaduje SharePoint soubory, které chcete nasadit serveru. Další informace najdete v tématu [stavebním blokem: řešení](http://go.microsoft.com/fwlink/?LinkID=169186).  
  
## <a name="feature-and-packaging-tool-support"></a>Funkce a podpora nástroje balení
 Nástroje pro vývoj služby SharePoint v sadě Visual Studio můžete použít k rychlé uspořádání souborů služby SharePoint do funkce a řešení balíčky pro nasazení. Nakonfigurování funkce a řešení můžete použít následující nástroje.  
  
-   Funkce návrháře a návrháři balíčku.  
  
-   Průzkumník balení, panel nástrojů.  
  
-   Průzkumník řešení.  
  
### <a name="feature-designer-and-package-designer"></a>Funkce návrháře a návrháři balíčku
 Můžete vytvořit funkce, nastavit obory a označit jiné funkce jako závislosti pomocí návrháře funkcí. Návrhář zobrazí také konečný soubor XML, který popisuje každou funkci. Další informace najdete v tématu [funkcí služby SharePoint vytvořit](../sharepoint/creating-sharepoint-features.md).  
  
 Použít funkci na určitý webový server nebo skupina webových serverů tak, že nastavíte její *oboru* v Návrháři funkce. Pokud se funkce aktivuje pro jednotlivé webové stránky, tato funkce funguje pouze v konkrétní webový server. Pokud se funkce aktivuje pro kolekci webů, položky ve funkci se vztahují celou kolekci webů. Další informace najdete v tématu [obor prvku](http://go.microsoft.com/fwlink/?LinkID=169189).  
  
 Pokud vaše funkce závisí na jiné funkce, můžete nastavit *závislost aktivace funkce* k označení závislé součásti před zpřístupněním vaši funkci. Závislost aktivace funkce ověří, pokud jsou v tomto oboru již aktivován závislé součásti. Další informace najdete v tématu [závislosti aktivace a oboru](http://go.microsoft.com/fwlink/?LinkID=169190).  
  
 V Návrháři balíčku můžete seskupit prvky SharePoint do jediného řešení balíček a nakonfigurovat, jestli se má resetovat webový server během nasazení. Pokud chcete nastavit typ serveru nasazení, použijte **vlastnosti** okna. Návrhář také vygeneruje soubor XML, který popisuje obsah balíčku. Další informace najdete v tématu [balíčků řešení služby SharePoint vytvořit](../sharepoint/creating-sharepoint-solution-packages.md).  
  
 Během nasazování zkopírujte soubory řešení na server SharePoint zastavení služby Internetové informační služby (IIS). Pomocí návrháře balíčků v sadě Visual Studio, můžete vybrat, zda webový server by měla být restartována. Chcete-li nakonfigurovat, pokud se řešení nasadí na front-end webovém serveru nebo aplikační server, použijte **vlastnosti** okna. Další informace najdete v tématu [prvek řešení (Solution)](http://go.microsoft.com/fwlink/?LinkID=169191).  
  
### <a name="packaging-explorer"></a>Průzkumník balení  
 K doplnění funkce návrháře a návrháři balíčku, můžete použít Průzkumník balení do skupiny souborů služby SharePoint do funkcí a balíčků. Kromě toho uvidí hierarchickým zobrazením Sharepointového projektu balíček, funkce, položky a soubory. Průzkumník balení je okno nástroje, který vám pomůže dokončit následující úlohy:  
  
- Otevřete položky Sharepointového projektu a soubory.  
  
- Přetažení položek projektu služby SharePoint z jednu funkci do jiného.  
  
- Přetažení položek projektu služby SharePoint a funkce z jednoho balíčku do jiného.  
  
- Přidáte novou funkci do balíčku.  
  
- Otevření Návrháře funkci nebo balíčku.  
  
- Ověření funkcí a balíčků.  
  
  Nástroje pro vývoj služby SharePoint v sadě Visual Studio mají ověřovacích pravidel pro zajištění, že je správně vytvořen balíček řešení. Kromě toho pravidla ověřte, že *.wsp* soubor řešení je možné úspěšně nasadit a aktivovat na Sharepointovém serveru. Další informace o schématu XML pro funkce, najdete v části [funkce schémata](http://go.microsoft.com/fwlink/?LinkID=169192).  
  
  Vlastní funkce a pravidel ověřování balíčku můžete přidat do systému Sharepointových projektů. Další informace najdete v tématu [postupy: vytvoření vlastní funkce a balíku ověřovacích pravidel pro řešení služby SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
  Další informace o Průzkumníku balíčků naleznete v tématu [postupy: Přidání nebo odebrání funkcí a položek z balíku pomocí Průzkumníku balíčků](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).  
  
### <a name="solution-explorer"></a>Průzkumník řešení
 Průzkumník řešení můžete použít k procházení a otevírání souborů projektu služby SharePoint. Chcete-li přidat funkce, přijímačů událostí funkce, pomocí místní nabídky v Průzkumníku řešení a zdroje funkcí. Kromě toho můžete otevřít funkce návrháře a návrháři balíčku konfigurace funkcí a balíčků pro nasazení.  
  
## <a name="deploy-sharepoint-solutions"></a>Nasazení řešení služby SharePoint
 Po přizpůsobení funkcí a balíčků v sadě Visual Studio, můžete vytvořit *.wsp* souborů k nasazení na servery služby SharePoint. Visual Studio můžete použít k ladění a testování. *wsp* pouze na serveru SharePoint ve vývojovém počítači. Další informace o tom, jak nasadit řešení služby SharePoint na vzdáleném serveru SharePoint, naleznete v tématu [nasazení řešení](http://go.microsoft.com/fwlink/?LinkID=169194).  
  
 Můžete také upravit kroky nasazení na vývojovém počítači. Další informace najdete v tématu [nasazení, publikování a upgradování balíčků řešení služby SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).  
  
## <a name="deploy-files-in-sharepoint-solutions"></a>Nasazení souborů v řešení služby SharePoint
 Obvykle když přidáte položku Sharepointového projektu do řešení služby SharePoint, všechny požadované soubory jsou zahrnuty. Soubory, které mohou být zkompilovány (soubory kódu) jsou integrované do výstupního sestavení řešení. Ale může také musíte přidat-zkompilovat soubory, například *.xml*, *.txt*, nebo soubory prostředků, do projektu služby SharePoint. Tyto soubory nejsou zabaleny automaticky v rámci vašeho řešení. Pokud chcete mít jistotu, že jsou zabaleny, přidat soubory pro mapovanou složku nebo položky Sharepointového projektu.  
  
 Soubory přidané do mapované složky se automaticky zkopírují do podregistru služby SharePoint, když se řešení nasadí. Soubory přidané do položky projektu služby SharePoint jsou nasazené do umístění zadaného ve **umístění nasazení** na základě vlastností pro každý soubor, který je částečně nastavena **typ nasazení** vlastnost. Ve výchozím nastavení **typ nasazení** hodnota vlastnosti je **NoDeployment**, což znamená, že soubor není nasazen s řešením. Je nutné nastavit jinou hodnotu pro vlastnost, která má soubor zahrnout do balíčku.  
  
 Například, chcete-li přidat *.xml* soubor do projektu služby SharePoint, proveďte jednu z těchto akcí:  
  
- Přidejte SharePoint "Rozložení" namapované složky do projektu. Tím se vytvoří v **Průzkumníka řešení** složku s názvem **rozložení** , která obsahuje podsložky pro projekt. Přidat *.xml* souboru do této nové podsložky. Ve výchozím nastavení je soubor nasazen do systému souborů služby SharePoint v části *... \TEMPLATE\LAYOUTS\\\<název složky >*. Informace o tom, jak přidat mapované složky najdete v tématu [postupy: Přidání a odebrání mapovaných složek](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
- Přidat *.xml* soubor do složky položky projektu služby SharePoint a potom změňte **typ nasazení** vlastnost *.xml* souboru z **NoDeployment**  další nastavení, jako **RootFile** nebo **ElementFile**. Odpovídající **typ nasazení** nastavení závisí na soubor a projekt. Další informace o **typ nasazení** naleznete v tématu Nastavení vlastností [řešení pro vývoj SharePoint](../sharepoint/developing-sharepoint-solutions.md).  
  
  Pokud je přidaný soubor se nedá použít u žádného konkrétního projektu v řešení, můžete přidat prázdný projekt SharePoint do vašeho řešení a potom k němu přidejte další soubory. Další alternativou k nasazení souborů pro službu SharePoint, zejména pro databázi obsahu, je přidat modul do projektu a pak přidat soubory do modulu. Další informace najdete v tématu [vložení souborů do řešení pomocí modulů](../sharepoint/using-modules-to-include-files-in-the-solution.md).  
  
## <a name="see-also"></a>Viz také:
 [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Sestavování a ladění řešení služby SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
