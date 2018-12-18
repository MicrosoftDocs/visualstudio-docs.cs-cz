---
title: Standardní Stereotypy pro modely UML | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML, stereotypes
- UML diagrams, stereotypes
ms.assetid: 8a8c2321-1cae-4ba8-bb9e-23495c3404d8
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 1fcc876a847429c0de9600a5a727b19334819119
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51763242"
---
# <a name="standard-stereotypes-for-uml-models"></a>Standardní stereotypy pro modely UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Přidávání stereotypů k elementům modelu UML na další informace pro čtečku, nebo pro počítač zpracování. Stereotypy, které jsou definovány v profilech a každý profil obsahuje sadu stereotypy. Pomocí sady Visual Studio jsou k dispozici několik profilů. Můžete také definovat vlastní profily, které mohou obsahovat vlastní stereotypy. Další informace najdete v tématu [definování profilu pro rozšíření UML](../modeling/define-a-profile-to-extend-uml.md).  
  
 Tuto funkci podporovat kterou verzí sady Visual Studio najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="the-standard-profiles"></a>Standardní profily  
 Následující profily jsou k dispozici v podporované edice sady Visual Studio, poté, co již byla nainstalována.  
  
|Profil|Účel|  
|-------------|-------------|  
|[L2 standardním profilu UML](#L2)|Standardní sadu Stereotypy, které je možné přidat další informace o elementu nebo relace.|  
|[L3 standardním profilu UML](#L3)|Standardní sadu Stereotypy, které je možné přidat další informace o elementu nebo relace.|  
|[Profil jazyka C#](#NetProfile)|Pokud máte v úmyslu třídu nebo jiný prvek v modelu UML představující programový kód, to lze naznačit jednomu stereotypu použitím z profil jazyka C#.<br /><br /> Tyto Stereotypy také přidání vlastností do prvky modelu.|  
  
 Když vytvoříte nový model UML, standardní L2 profilů UML a L3 jsou propojeny s modelem, dokud neodeberete odkazy.  
  
 Použít stereotypy v některém z těchto profilů, je třeba nejprve na balíček nebo model, který obsahuje požadované prvky a aplikovat je na propojit profil.  
  
#### <a name="to-link-a-profile-to-a-model-or-a-package"></a>Odkaz na model nebo balíček profilu  
  
1.  Otevřít **Průzkumníku modelů UML**. Na **architektura** nabídky, přejděte k **Windows**a potom klikněte na tlačítko **Průzkumníku modelů UML**.  
  
2.  Vyhledejte balíček nebo model, který obsahuje všechny prvky, na které budete chtít použít stereotypy v profilu.  
  
3.  Klikněte pravým tlačítkem na balíček nebo model a pak klikněte na tlačítko **vlastnosti**.  
  
4.  V **vlastnosti** okno, nastaveno **profily** vlastnost profily, které chcete.  
  
#### <a name="to-remove-the-link-between-a-profile-and-a-model-or-package"></a>Odebere propojení mezi profil a model nebo balíček  
  
1.  V Průzkumníku modelů UML, klikněte pravým tlačítkem na model nebo balíček a pak klikněte na tlačítko **vlastnosti**.  
  
2.  V okně Vlastnosti nastavte **profily** vlastnost prázdná.  
  
    > [!NOTE]
    >  Profil, který lze odpojit pouze v případě, že žádný z elementů v modelu nebo balíček použít tento profil stereotypy.  
  
#### <a name="to-apply-a-stereotype-to-a-model-element"></a>Chcete-li použít stereotyp na prvek modelu  
  
1.  Klikněte pravým tlačítkem myši na prvek modelu v diagramu nebo v **Průzkumníku modelů UML**a potom klikněte na tlačítko **vlastnosti**.  
  
2.  Klikněte na tlačítko **Stereotypy** vlastnosti a vyberte Stereotypy, které chcete použít.  
  
     Vybrané Stereotypy se zobrazí v rámci "odlišené dvojitou» v prvku modelu pro většinu typů element.  
  
    > [!NOTE]
    >  Pokud nevidíte **Stereotypy** vlastnost, nebo pokud chcete stereotyp nezobrazí, ověřte, zda prvek modelu je uvnitř balíčku nebo modelu, ke kterému je propojená příslušný profil.  
  
3.  Některé Stereotypy umožní nastavit hodnoty dalších vlastností pro ovládací prvek modelu. Chcete-li zobrazit tyto vlastnosti, rozbalte **Stereotypy** vlastnost.  
  
###  <a name="L2"></a> L2 standardním profilu UML  
 Následující Stereotypy umožňuje specialize význam elementů modelu UML, pokud odkaz na profil, který byl odebrán z modelu.  
  
 Přesné význam těchto Stereotypy je určena vlastní místní konvence a všechny nástroje, které můžete použít ke zpracování modelu.  
  
|Stereotyp|Platí pro|Význam|  
|----------------|----------------|-------------|  
|pomocné|Třída|Třída, která podporuje jiné třídy, obvykle prostřednictvím implementace další logiku. Jiná třída může mít stereotyp "aktivní".|  
|– volání|Závislost|Klientská třída volá operace od dodavatele.|  
|vytvoření|Závislost|Klientská třída vytváří instance dodavatele.|  
|vytvoření|Zpráva|Odesílatel vytvoří příjemce.|  
|vytvoření|Operace|Tato operace je konstruktor.|  
|odvození|Závislost|Element klienta je vypočítán zcela nebo částečně od dodavatele.|  
|zrušení|Operace|Operace odstraní jeho instanci.|  
|dokument|Artefakt|A "souboru", který je není zdrojem nebo spustitelný soubor.|  
|entita|Součást|Součást představuje obchodní koncept.|  
|spustitelný soubor|Artefakt|Spustitelný soubor "file".|  
|– soubor|Artefakt|Fyzický soubor.|  
|fokus|Třída|Třída definující základní obchodní logiku, která podporuje několik "pomocné" třídy.|  
|rozhraní|Balíček|Tento balíček definuje opakovaně návrhovém vzoru.|  
|Implementace|Součást|Implementace "specifikace".|  
|implementationClass|Třída|Tato třída Popisuje implementaci a každá instance modulu runtime má jednu třídu pevné implementace. Oproti "typ".|  
|Vytvoření instance|Závislost|Klient vytvoří instance dodavatele.|  
|knihovna|Artefakt|Knihovna "file".|  
|metaclass|Třída|Instance této třídy jsou zároveň třídami.|  
|modelLibrary|Balíček|Obsahuje elementy modelu měli v úmyslu opakovaně využít pro import balíčků. Obvykle definovali jako součást profilu a automaticky importovány pomocí aplikace profilu.|  
|zpracování|Součást|Komponenta založenou na transakcích, nebo který vlákno.|  
|realizace|Třída, rozhraní, součástí|Popisuje implementaci.|  
|Upřesnit|Závislost|Klientská třída, komponenty nebo balíček poskytuje další informace o specifikaci nebo návrhu než od dodavatele.|  
|Odpovědnosti|Závislost|Komentář na konci dodavatele závislost definuje odpovědnosti třída klienta nebo komponenty.|  
|skript|Artefakt|Interpretovatelném "soubor".|  
|Odeslat|Závislost|Zdroj operace odešle cíl signálu.|  
|service|Součást|Bezstavové komponenty.|  
|source|Artefakt|Kompilovat "soubor".|  
|specifikace|Třída, rozhraní, součástí|Definuje chování komponenty nebo objektu bez definování, jak to funguje interně.|  
|Subsystém|Součást|Součástí rozsáhlém systému. Subsystém na diagramu případu použití je komponenta s stereotyp subsystému.|  
|trasování|Závislost|Element klient je součástí návrhu, která provádí od dodavatele. Dva elementy end třídy této závislosti jsou obvykle v různých modelech. Jedním z těchto modelů je realizace druhé.|  
|– typ|Třída|Určuje chování objektu s informacemi o tom, jak je implementován. Objekt je členem typu, pokud odpovídá specifikaci.|  
|nástroj|Třída|Kolekce statické funkce. Třída nemá žádné instance.|  
  
###  <a name="L3"></a> L3 standardním profilu UML  
 Následující Stereotypy umožňuje specialize význam elementů modelu UML, není-li profil, který se odpojil z modelu.  
  
 Přesné význam těchto Stereotypy je určena vlastní místní konvence a všechny nástroje, které můžete použít ke zpracování modelu.  
  
|Stereotyp|Platí pro|Popis|  
|----------------|----------------|-----------------|  
|buildComponent|Součást|Kolekce prvků, které slouží k definování sestavení.|  
|metaModel|Model|Definuje Modelovací jazyk, jako je například hodnotu typu variant UML nebo jazyka specifického pro doménu.|  
|systemModel|Model|Model, který je kolekce modelů, které se vztahují na stejném systému, například specifikace, realizace a trasování vztahy mezi nimi.|  
  
##  <a name="NetProfile"></a> Profil jazyka C#  
 Stereotypy definované v tomto profilu umožňují určit, že prvek modelu je určená pro překlad do kódu programu. Každý stereotyp definuje další vlastnosti, které můžete nastavit na prvek modelu.  
  
 Chcete-li zpřístupnit tyto Stereotypy, propojte model nebo balíček profil jazyka C#. Prvky modelu v tomto modelu nebo balíček lze následně použít stereotypy.  
  
 K dispozici Stereotypy prvky, na které se vztahují, a další vlastnosti, které využívají k dispozici jsou shrnuty v následující tabulce.  
  
|Stereotyp|Platí pro|Vlastnosti|  
|----------------|----------------|----------------|  
|**Třída jazyka C#**|Třída UML<br /><br /> Součást|**Atributy CLR**<br /><br /> **Je částečná**<br /><br /> **Je zapečetěná**<br /><br /> **Je statická**<br /><br /> **Nebezpečná**<br /><br /> **Viditelnost balíčku**|  
|**Struktura jazyka C#**|Třída UML<br /><br /> Součást|**Atributy CLR**<br /><br /> **Je částečná**<br /><br /> **Nebezpečná**<br /><br /> **Viditelnost balíčku**|  
|**Globální členové C#**|Třída UML<br /><br /> Součást|**Atributy CLR**|  
|**Rozhraní jazyka C#**|Rozhraní UML|**Atributy CLR**<br /><br /> **Je částečná**<br /><br /> **Viditelnost balíčku**|  
|**Výčet jazyka C#**|Výčet UML|**ClrAttributes**<br /><br /> **Základní typ**|  
|**Obor názvů C#**|Balíček UML|**Atributy CLR**<br /><br /> **Základní název**<br /><br /> **Použití oboru názvů**|  
  
## <a name="see-also"></a>Viz také  
 [Přidávání stereotypů k elementům modelu UML](../modeling/add-stereotypes-to-uml-model-elements.md)   
 [Přizpůsobení modelu pomocí profilů a stereotypů](../modeling/customize-your-model-with-profiles-and-stereotypes.md)   
 [Definování profilu pro rozšíření UML](../modeling/define-a-profile-to-extend-uml.md)



