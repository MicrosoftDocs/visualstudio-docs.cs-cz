---
title: Třídy jazyka Visual C++ v Návrháři tříd | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.classdesigner.inheritancelinelabel
helpviewer_keywords:
- Class Designer [Visual Studio], classes
ms.assetid: 75e56f8c-11ef-42a3-b7ec-3d2cf25c581b
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d4193dda70aeda8534b9dc2fa3428ca08a9d89fa
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49285685"
---
# <a name="visual-c-classes-in-class-designer"></a>Třídy jazyka Visual C++ v návrháři tříd
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Návrhář tříd podporuje C++ třídy a vizualizuje nativních tříd jazyka C++ stejně jako obrazců třídy jazyka Visual Basic a Visual C#, s tím rozdílem, že třídy C++ mohou mít více vztahů dědičnosti. Můžete rozbalit obrazec třídy na Zobrazit další pole a metody ve třídě nebo sbalit uchovejte prostor na disku.  
  
> [!NOTE]
>  Návrhář tříd nepodporuje sjednocení (speciální typ třídy, ve kterém paměť přidělena je pouze množství potřebné pro unie největší datový člen).  
  
## <a name="simple-inheritance"></a>Jednoduchá dědičnost  
 Když přetáhnout více než jednu třídu do diagramu třídy a třídy mají vztah dědičnosti třídy, je šipka připojuje. Šipka body ve směru základní třídy. Například následující třídy jsou zobrazeny v diagramu tříd, šipka připojí, přejdete na b A:  
  
```  
class A {};  
class B : A {};  
```  
  
 Můžete také přetáhnout do diagramu tříd pouze třídy B, B pravým tlačítkem myši na obrazec třídy a pak klikněte na tlačítko **zobrazit základní třídy**. Zobrazí se její základní třídě: A.  
  
## <a name="multiple-inheritance"></a>Vícenásobná dědičnost  
 Návrhář tříd podporuje vizualizaci vztahů dědičnosti více tříd. *Vícenásobná dědičnost* se používá při odvozená třída má atributy více než jedné základní třídy. Tady je příklad vícenásobné dědičnosti:  
  
```  
class Bird {};  
class Swimmer {};  
class Penguin : public Bird, public Swimmer {};  
```  
  
 Přetáhněte více než jednu třídu do diagramu třídy a třídy mají vztah dědičnosti třídy více, šipka propojí je. Šipka body ve směru ze základních tříd.  
  
 Pravým tlačítkem myši na tvar třídy a pak levým na **zobrazit základní třídy** zobrazuje základní třídy, které pro vybranou třídu.  
  
> [!NOTE]
>  **Zobrazit odvozené třídy** příkaz není podporován pro kód C++. Lze zobrazit odvozené třídy tak, že přejdete na zobrazení tříd, rozbalení uzlu typu, rozšíření **odvozené typy** podsložky a následným přetažením tyto typy do diagramu tříd.  
  
 Další informace o dědičnosti více tříd, naleznete v tématu [vícenásobná dědičnost (NOTINBUILD)](http://msdn.microsoft.com/en-us/3b74185e-2beb-4e29-8684-441e51d2a2ca) a [více základních tříd](http://msdn.microsoft.com/library/a30c69fe-401c-4a87-96a0-e0da70c7c740).  
  
## <a name="abstract-classes"></a>Abstraktní třídy  
 Návrhář tříd podporuje abstraktních tříd (také s názvem "základních tříd abstraktu"). Toto jsou třídy, která nikdy vytvořit instanci, ale ze které odvozujete jiné třídy. Použijeme příklad z "Vícenásobné dědičnosti" dříve v tomto dokumentu, které může vytvořit instanci `Bird` třídy jako jednotlivé objekty následujícím způsobem:  
  
```  
int main()  
{  
   Bird sparrow;  
   Bird crow;  
   Bird eagle;  
}  
```  
  
 Ale možná chcete vytvořit instanci `Swimmer` třídu jako jednotlivé objekty. Možná chcete pouze odvozovat další typy jsou třídy, například `Penguin`, `Whale`, a `Fish`. V takovém případě by deklarace `Swimmer` třídu jako abstraktní základní třídu.  
  
 Chcete-li deklarovat třídu jako abstraktní, můžete použít `abstract` – klíčové slovo. Členy označené jako abstraktní, nebo součástí abstraktní třídu, jsou virtuální a musí být implementované třídami, které jsou odvozeny od abstraktní třídy.  
  
```  
class Swimmer abstract  
{  
   virtual void swim();  
   void dive();  
};  
```  
  
 Můžete také deklarovat třídu jako abstraktní vložením alespoň jednu prázdnou virtuální funkci:  
  
```  
class Swimmer  
{  
   virtual void swim() = 0;  
   void dive();  
};  
```  
  
 Při zobrazení tyto deklarace v diagramu tříd, název třídy `Swimmer` a čistě virtuální funkce `swim` v zobrazí kurzívou v obrazce abstraktní třídu, společně s zápis **abstraktní třída**. Všimněte si, že tvar typu abstraktní třídy je stejné jako u běžné třídy, s tím rozdílem, že jeho ohraničení se tečkovaná čára.  
  
 Třídy odvozené od abstraktní základní třída musí přepsat všechny čistě virtuální funkce v základní třídě, nebo odvozené třídy se nedá vytvořit instance. Ano, třeba při odvozování `Fish` třídy z `Swimmer` třídy, `Fish` musí přepsat `swim` metody:  
  
```  
class Fish : public Swimmer  
{  
   void swim(int speed);  
};  
  
int main()  
{  
   Fish guppy;  
}  
```  
  
 Tento kód se zobrazí v diagramu tříd, návrhář tříd kreslení čáru dědičnosti z `Fish` k `Swimmer`.  
  
## <a name="anonymous-classes"></a>Anonymní třídy  
 Návrhář tříd podporuje anonymní třídy. *Anonymní typy třídy* tříd jsou deklarovány bez identifikátoru. Jejich nemůže mít konstruktor nebo destruktor, nelze předat jako argumenty funkce a nemůže být vrácen jako návratové hodnoty ve funkcích. Anonymní třídy lze použít k nahrazení názvu třídy s názvem definice typedef, jako v následujícím příkladu:  
  
```  
typedef struct  
{  
    unsigned x;  
    unsigned y;  
} POINT;  
```  
  
 Struktury také mohou být anonymní. Návrhář tříd zobrazí anonymní třídy a struktury stejné jako zobrazení příslušného typu. I když můžete deklarovat a zobrazení anonymní třídy a struktury, nebude návrhář tříd použít název značky, který zadáte. Použije název, který generuje zobrazení tříd. Třídy nebo struktury se zobrazí v zobrazení tříd a návrhář tříd jako element volá **__unnamed**.  
  
 Další informace o anonymních tříd naleznete v tématu [anonymní typy třídy](http://msdn.microsoft.com/library/9ba667b2-8c2a-4c29-82a6-fa120b9233c8).  
  
## <a name="template-classes"></a>Třídy šablon  
 Návrhář tříd podporuje vizualizaci tříd šablon. Vnořené deklarace jsou podporovány. Následující tabulka uvádí některé typické deklarace.  
  
|Element kódu|Zobrazení návrháře tříd|  
|------------------|-------------------------|  
|`template <class T>`<br /><br /> `class A {};`|`A<T>`<br /><br /> Třída šablony|  
|`template <class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Třída šablony|  
|`template <class T, int i>`<br /><br /> `class A {};`|`A<T, i>`<br /><br /> Třída šablony|  
|`template <class T, template <class K> class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Třída šablony|  
  
 V následující tabulce jsou uvedeny některé příklady částečná specializace.  
  
|Element kódu|Zobrazení návrháře tříd|  
|------------------|-------------------------|  
|`template<class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Třída šablony|  
|`template<class T>`<br /><br /> `class A<T, T> {};`|`A<T, T>`<br /><br /> Třída šablony|  
|`template <class T>`<br /><br /> `class A<T, int> {};`|`A<T, int>`<br /><br /> Třída šablony|  
|`template <class T1, class T2>`<br /><br /> `class A<T1*, T2*> {};`|`A<T1*, T2*>`<br /><br /> Třída šablony|  
  
 V následující tabulce jsou uvedeny příklady dědičnosti v částečné specializaci.  
  
|Element kódu|Zobrazení návrháře tříd|  
|------------------|-------------------------|  
|`template <class T, class U>`<br /><br /> `class A {};`<br /><br /> `template <class TC>`<br /><br /> `class A<T, int> {};`<br /><br /> `class B : A<int, float>`<br /><br /> `{};`<br /><br /> `class C : A<int, int>`<br /><br /> `{};`|`A<T, U>`<br /><br /> Třída šablony<br /><br /> `B`<br /><br /> Třída<br /><br /> (bodů na třídy A)<br /><br /> `C`<br /><br /> Třída<br /><br /> (bodů na třídy A)|  
  
 V následující tabulce jsou uvedeny příklady částečná specializace šablony funkce.  
  
|Element kódu|Zobrazení návrháře tříd|  
|------------------|-------------------------|  
|`class A`<br /><br /> `{`<br /><br /> `template <class T, class U>`<br /><br /> `void func(T a, U b);`<br /><br /> `template <class T>`<br /><br /> `void func(T a, int b);`<br /><br /> `};`|`A`<br /><br /> Func\<T, U > (+ 1 přetížení)|  
|`template <class T1>`<br /><br /> `class A {`<br /><br /> `template <class T2>`<br /><br /> `class B {};`<br /><br /> `};`<br /><br /> `template<> template<>`<br /><br /> `class A<type>::B<type> {};`|`A<T1>`<br /><br /> Třída šablony<br /><br /> `B<T2>`<br /><br /> Třída šablony<br /><br /> (B je obsažen v rámci třídy A v části **vnořené typy**)|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `class A : C<int> {};`|`A`<br /><br /> Třída<br /><br /> -> C\<int ><br /><br /> `C<T>`<br /><br /> Třída šablony|  
  
 V následující tabulce jsou uvedeny příklady šablony dědičnosti.  
  
|Element kódu|Zobrazení návrháře tříd|  
|------------------|-------------------------|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {`<br /><br /> `class B {};`<br /><br /> `}`<br /><br /> `class A : C<int>::B {};`|`A`<br /><br /> Třída<br /><br /> ->B<br /><br /> `C<int>`<br /><br /> Třída<br /><br /> (B je obsažen v rámci třídy C v rámci **vnořené typy**)<br /><br /> `C<T>`<br /><br /> Třída šablony|  
  
 V následující tabulce jsou uvedeny příklady canonical specializované třídy připojení.  
  
|Element kódu|Zobrazení návrháře tříd|  
|------------------|-------------------------|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {};`<br /><br /> `class A : C<int> {};`<br /><br /> `class D : C<float> {};`|`A`<br /><br /> Třída<br /><br /> -> C\<int ><br /><br /> `C<int>`<br /><br /> Třída<br /><br /> `C<T>`<br /><br /> Třída šablony<br /><br /> `D`<br /><br /> Třída<br /><br /> -> C\<float >|  
|`class B {`<br /><br /> `template <class T>`<br /><br /> `T min (const T &a, const T &b);`<br /><br /> `};`|`B`<br /><br /> min \<T >|  
  
## <a name="see-also"></a>Viz také  
 [Práce s kódem jazyka Visual C++ (návrhář tříd)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [Třídy a struktury](http://msdn.microsoft.com/library/516dd496-13fb-4f17-845a-e9ca45437873)   
 [Anonymní typy třídy](http://msdn.microsoft.com/library/9ba667b2-8c2a-4c29-82a6-fa120b9233c8)   
 [(NOTINBUILD) Vícenásobná dědičnost](http://msdn.microsoft.com/en-us/3b74185e-2beb-4e29-8684-441e51d2a2ca)   
 [Vícenásobné třídy Base](http://msdn.microsoft.com/library/a30c69fe-401c-4a87-96a0-e0da70c7c740)   
 [Šablony](http://msdn.microsoft.com/library/90fcc14a-2092-47af-9d2e-dba26d25b872)



