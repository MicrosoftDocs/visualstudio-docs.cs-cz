---
title: Prostředí (izolované nebo integrované) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell
- Visual Studio, Shell
- Shell [Visual Studio]
- Visual Studio shell, shell-based applications
- Shell [Visual Studio], shell-based applications
ms.assetid: c64a9bf0-9bf8-45c3-8fa2-306fa6cab66a
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 856e32d4569e5dcb73e783d0a6b66e186fbb1848
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755886"
---
# <a name="shell-isolated-or-integrated"></a>Prostředí (izolované nebo integrované)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vytvoření sady Visual Studio na základě aplikace v režimu integrované nebo izolované. V integrovaném režimu mnoho funkcí sady Visual Studio jsou k dispozici kromě vaší aplikace. V izolovaném režimu si zvolíte dílčí skupinu funkcí nástroje Visual Studio, které chcete distribuovat spolu se svým vlastním rozšířením.  
  
## <a name="integrated-mode"></a>Integrovaný režim  
 Integrovaný režim umožňuje uživatelům používat standardní funkce sady Visual Studio spolu s vlastní nástroje. Integrované prostředí je určený primárně pro hostování programovacích jazyků a nástrojů pro vývoj softwaru.  
  
 Vlastní nástroje, které jsou založené na prostředí integrated shell automaticky sloučit s jinou edici sady Visual Studio, který je nainstalovaný na stejném počítači. Distribuovatelné součásti verzi sady Visual Studio integrované prostředí můžete zadat, pokud ještě není nainstalované Visual Studio.  
  
 Distribuovatelné součásti verzi prostředí sady Visual Studio integrované nezahrnuje programovacích jazyků a funkcí pro podporu systémů jejich příslušného projektu.  
  
> [!NOTE]
>  Režim integrovaného prostředí Visual Studio je možné nainstalovat společně s všechny edice sady Visual Studio s výjimkou edice Express.  
  
 Další informace najdete v tématu [Visual Studio Shell (integrovaný režim)](../extensibility/visual-studio-shell-integrated.md).  
  
## <a name="isolated-mode"></a>Izolovaný režim  
 Izolovaný režim vám umožní vytvořit vlastní nástroje, na kterých běží vedle sebe s jinými verzemi nástroje Visual Studio. Je určená primárně pro nástroje, které mají přístup ke službám Visual Studio bez v závislosti na všechny standardní funkce sady Visual Studio. Můžete přizpůsobit vzhled aplikace založené na prostředí sady Visual Studio izolované. Snadno můžete vypnout funkcí a příkaz skupiny nabídek, které nechcete, aby se zobrazí spolu s aplikací.  
  
 Další informace najdete v tématu [izolované prostředí sady Visual Studio](../extensibility/visual-studio-isolated-shell.md).  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>Distribuce vaší aplikace integrované nebo izolované prostředí  
 Integrované nebo izolované prostředí se aplikace dala distribuovat, budete muset zahrnout aplikace, speciální integrované nebo izolované prostředí distribuovatelné součásti a instalační program. Další informace o distribuci a instalaci najdete v tématu [distribuce aplikací izolovaného prostředí](../extensibility/distributing-isolated-shell-applications.md).  
  
> [!IMPORTANT]
>  [Licenční smlouvy koncovým uživatelem (EULA)](https://www.visualstudio.com/en-us/support/legal/mt171552) pro Visual Studio integrované a izolované prostředí obsahuje oddíl na shromažďování dat (**části 3. Data**).  Popisuje zákaznická data využití, které může společnost Microsoft shromažďovat od uživatelů buď integrované nebo izolované prostředí softwaru, který jste vytvořili do vaší aplikace. Další informace najdete v tématu [prohlášení společnosti Microsoft Visual Studio Product řady](https://www.visualstudio.com/en-us/dn948229).  
> 
>  Budete-li shromažďovat data o využití samostatné od svých zákazníků prostřednictvím vaší aplikace, musíte zadat příslušné oznámení pro uživatele vaší aplikace můžete shromažďovat.  Při distribuci softwaru izolované nebo integrované prostředí v rámci vaší aplikace, podle této licence Visual Studio Software Development Kit, musí obsahovat jednu z následujících akcí:  
> 
> - Licenční smlouva koncového uživatele jako součást vaší licence aplikace  
>   -   vaše vlastní smlouva EULA, který vyžaduje, aby vaši zákazníci souhlas s podmínkami, které chrání aplikace Visual Studio integrované nebo izolované prostředí alespoň tolik jako koncový uživatel licenční podmínky společnosti Microsoft pro software prostředí  
  
## <a name="additional-resources"></a>Další prostředky  
 Další informace o distribuovatelných balíčků naleznete v tématu [stahování rozšíření sady Visual Studio](http://go.microsoft.com/fwlink/?LinkID=119298) webu.  
  
## <a name="see-also"></a>Viz také  
 [Odesílání rozšíření sady Visual Studio](../extensibility/shipping-visual-studio-extensions.md)

