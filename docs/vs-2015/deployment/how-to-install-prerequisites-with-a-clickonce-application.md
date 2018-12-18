---
title: 'Postupy: instalace předpokladů s aplikací ClickOnce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], prerequisites
- prerequisites, ClickOnce
- components, bootstrapping
ms.assetid: e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 47d4355fc1b5690d6c9c76fd354a5f5bd4830d8e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49196284"
---
# <a name="how-to-install-prerequisites-with-a-clickonce-application"></a>Postupy: Instalace předpokladů s aplikací ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Všechny [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace vyžadují v počítači je nainstalována správná verze rozhraní .NET Framework, než budou moci spustit; mnohé aplikace mají také další požadavky. Při publikování [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace, můžete použít sadu součásti, které mají být zabaleny spolu s vaší aplikace. Při instalaci se provede kontrola pro každý požadavek k určení, zda je již existuje; Pokud nebude třeba nainstalovat před instalací [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace.  
  
 Místo vytváření balíčků a publikování požadavky, můžete také zadat umístění pro stahování pro součásti. Například místo včetně předpokladů s každou aplikaci, kterou publikujete, můžete použít sdílené centralizovaného nebo umístění webu, který obsahuje instalační programy pro všechny vaše požadavky, během instalace, se stáhnou součásti a nainstalovat z tohoto umístění.  
  
> [!IMPORTANT]
>  Před publikováním poprvé, měli byste přidat balíčky Instalační program požadovaných součástí na vývojovém počítači [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace. Další informace najdete v tématu [jak: zahrnují předpokladů s aplikací ClickOnce](../deployment/how-to-include-prerequisites-with-a-clickonce-application.md).  
  
 Požadavky jsou spravovány v **požadavky** dialogové okno, přístupné **publikovat** podokně **Návrháře projektu**.  
  
> [!NOTE]
>  Kromě předem určený seznam požadavky můžete přidat vlastní komponenty do seznamu. Další informace najdete v tématu [vytváření balíčků Bootstrapperu](../deployment/creating-bootstrapper-packages.md).  
  
### <a name="to-specify-prerequisites-to-install-with-a-clickonce-application"></a>Chcete-li určit požadavky pro instalaci s aplikací ClickOnce  
  
1.  S projekt vybraný v **Průzkumníka řešení**na **projektu** klikněte na nabídku **vlastnosti**.  
  
2.  Vyberte **publikovat** podokně.  
  
3.  Klikněte na tlačítko **požadavky** tlačítko Otevřít **požadavky** dialogové okno.  
  
4.  V **požadavky** dialogové okno pole, ujistěte se, že **vytvořit instalační program pro nainstalování nezbytných součástí** je zaškrtnuto políčko.  
  
5.  V **požadavky** seznamu, zkontrolujte součásti, které chcete nainstalovat a potom klikněte na **OK**.  
  
     Vybrané součásti se zabalit a publikovat spolu s vaší aplikace.  
  
### <a name="to-specify-a-different-download-location-for-prerequisites"></a>Chcete-li určit různá umístění pro nainstalování součástí  
  
1.  S projekt vybraný v **Průzkumníka řešení**na **projektu** klikněte na nabídku **vlastnosti**.  
  
2.  Vyberte **publikovat** podokně.  
  
3.  Klikněte na tlačítko **požadavky** tlačítko Otevřít **požadavky** dialogové okno.  
  
4.  V **požadavky** dialogové okno pole, ujistěte se, že **vytvořit instalační program pro nainstalování nezbytných součástí** je zaškrtnuto políčko.  
  
5.  V **Zadejte prosím umístění pro nainstalování součástí** vyberte **stáhnout nezbytné součásti z následujícího umístění**.  
  
6.  Z rozevíracího seznamu vyberte umístění nebo zadejte adresu URL, cestu k souboru nebo umístění FTP a klikněte na **OK.**  
  
    > [!NOTE]
    >  Ujistěte se, že existují instalační programy pro zadanou součástí v zadaném umístění.  
  
## <a name="see-also"></a>Viz také  
 [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Postupy: Publikování aplikace ClickOnce pomocí průvodce publikováním](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)



