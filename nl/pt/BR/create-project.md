---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-18"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

Essa documentação destina-se ao {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud}}. Para ver a documentação para a versão anterior do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace, [clique neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/docs/services/knowledge-studio/create-project.html){: new_window}.
{: tip}

# Criando uma área de trabalho
{: #create-project}

A primeira etapa da criação de um modelo customizado é criar uma área de trabalho.
{: shortdesc}

## Sobre essa Tarefa

Para cada modelo que deseja construir e usar, você cria uma única área de trabalho que contém os artefatos e recursos necessários para construir o modelo. Em seguida, você treina o modelo para produzir um modelo customizado que pode ser implementado em um serviço externo para uso.

Antes de criar uma área de trabalho, responda a estas perguntas:

- **Que tipo de modelo você deseja criar?**

    - Modelo de aprendizado de máquina: usa a abordagem estatística para localizar entidades e relacionamentos em documentos. Esse tipo de modelo pode se adaptar conforme a quantia de dados cresce.
    - Modelo baseado em regra: usa uma abordagem declarativa para localizar entidades em documentos. Esse tipo de modelo é mais previsível e é mais fácil de entender e manter. No entanto, ele não aprende em dados novos. Só é possível localizar padrões que ele foi ensinado a procurar.

    > **Nota:** também é possível criar uma área de trabalho que contém um modelo baseado em regra e um modelo de aprendizado de máquina.

- **Quais serviços usarão o modelo?**

    Veja [Integração de serviços do {{site.data.keyword.watson}}](/docs/services/watson-knowledge-studio/index.html#wks_watsoninteg) para obter informações sobre os outros serviços do {{site.data.keyword.watson}} com os quais os modelos customizados podem ser usados.

## Procedimento

Para criar uma área de trabalho, conclua as etapas a seguir:

1. Efetue login como um administrador do {{site.data.keyword.knowledgestudioshort}} e clique em **Criar área de trabalho**.

    > **Nota:** as pessoas com a função de gerente de projeto podem executar quase todas as tarefas, exceto criar uma área de trabalho. Um administrador deve criar a área de trabalho inicialmente e designar gerentes de projeto a ela.

1. Dê a área de trabalho um nome. Escolha um nome abreviado que reflita seu conteúdo de domínio ou o propósito do modelo. Se você precisar, será possível mudar o nome da área de trabalho mais tarde.
1. Identifique a linguagem dos documentos em sua área de trabalho. Os documentos que você inclui na área de trabalho e os dicionários que cria ou faz upload devem estar na linguagem especificada.
1. Opcional: se você deseja mudar o tokenizer que é usado pelo aplicativo do tokenizer baseado em aprendizado de máquina padrão, é possível expandir a seção **Opções avançadas** e escolher **Tokenizer baseado em dicionário**.

    O tokenizer padrão é mais avançado do que o tokenizer baseado em dicionário; ele usa aprendizado de máquina para identificar os tokens nos documentos de origem com base no aprendizado estatístico que foi feito na linguagem dos documentos de origem. Ele identifica tokens com mais precisão, pois entende os padrões mais naturais e sutis de linguagem. O tokenizer baseado em dicionário identifica tokens com base nas regras de linguagem. Veja [Tokenizers](/docs/services/watson-knowledge-studio/create-project.html#wks_tokenizer) para obter mais detalhes.

1. Opcional: se você deseja incluir gerenciadores de projeto na área de trabalho, expanda a seção **Opções avançadas** e selecione na lista os nomes das pessoas que você deseja incluir como gerentes de projeto. O administrador pode incluir ou remover gerentes de projeto posteriormente, editando a área de trabalho.

    Somente os nomes de pessoas que você designou à função de gerente de projeto na página Gerenciamento de conta do usuário para a instância são exibidos. Veja [Montando uma equipe](/docs/services/watson-knowledge-studio/team.html) para obter mais informações sobre como incluir usuários.

    > **Nota:** se você tiver uma assinatura do plano Lite, ignore esta etapa. Não é possível incluir outros usuários, então não é possível designar ninguém à função de gerente de projeto. Você não precisa de um gerente de projeto separado. Como um administrador, é possível executar todas as tarefas que um gerente de projeto normalmente executaria.

1. Clique em **Criar**.

## O que fazer em seguida

Após a área de trabalho ser criada, é possível começar a configurar os recursos da área de trabalho.

Para mudar a descrição da área de trabalho ou o nome da área de trabalho ou para incluir ou remover gerentes de projeto mais tarde, um administrador pode editar a área de trabalho. Na página inicial do {{site.data.keyword.knowledgestudioshort}}, clique no ícone **Mostrar menu** no tile da área de trabalho e escolha a opção de menu **Editar**.

**Conceitos relacionados**:

[Fazendo upload de recursos de outra área de trabalho](/docs/services/watson-knowledge-studio/exportimport.html)

**Referência relacionada**:

[Suporte ao idioma](/docs/services/watson-knowledge-studio/language-support.html)

## Tokenizers
{: #wks_tokenizer}

Um tokenizer agrupa caracteres em tokens e tokens em sentenças. Um token é fracamente equivalente a uma palavra.

As ações que um tokenizer deve tomar para identificar os tokens de um documento diferem dependendo da linguagem do documento. Em inglês, os tokens são frequentemente comparados a palavras como delimitados por espaços em branco em uma sentença. No entanto, eles nem sempre correspondem um a um com palavras; outros elementos textuais são considerados tokens em algumas situações. Por exemplo, a pontuação no término de uma sentença é considerada um token e as contrações são frequentemente expandidas em dois tokens. Em linguagens que não usam espaços em branco, como chinês, algoritmos estatísticos mais complicados são usados para identificar os tokens.

O processo de tokenização é importante porque ele determina os grupos de caracteres que os usuários podem destacar para anotação no editor de verdade absoluta. As anotações de entidade e menções de relação geralmente são alinhadas com limites de token e devem ser rotuladas dentro de uma sentença; elas não podem abranger limites de sentença.

### Tipos suportados

O {{site.data.keyword.knowledgestudioshort}} suporta os tokenizers a seguir:

- **Tokenizer baseado em aprendizado de máquina (padrão)**

    Este é um tokenizer mais avançado que identifica os tokens nos documentos de origem com base no aprendizado estatístico que ele fez na linguagem dos documentos de origem. Esse tokenizer localiza tokens que capturam os padrões mais naturais e sutis de linguagem. Não é possível customizar esse tokenizer.

- **Tokenizer baseado em dicionário**

    Este tokenizer é baseado em dicionários linguísticos. Ele localiza tokens que seguem as regras da linguagem de documento de origem. Somente usuários avançados podem customizar este tokenizer.

Deve-se escolher o tokenizer que você deseja usar ao criar a área de trabalho. Não é possível alternar para um tokenizer diferente mais tarde. Para obter resultados melhores, use o tokenizer padrão. Somente usuários avançados que desejam modificar o comportamento de tokenizer por meio de um mecanismo de dicionário determinístico podem escolher o tokenizer baseado em dicionário. Eles podem então customizá-lo incluindo novas entradas no dicionário. Entretanto, a customização deve ser feita com cuidado porque quando você inclui novas palavras no dicionário, as mudanças podem afetar o modelo de aprendizado de máquina de maneiras indesejadas.

## Resumo de entradas, saídas e limitações
{: #wks_formats}

Os diferentes estágios de desenvolvimento de modelo requerem entradas diferentes e produzem saídas diferentes.

Para cada etapa do processo de desenvolvimento de modelo, esta tabela resume as atividades típicas que você executa, os formatos de arquivo de entrada suportados, as saídas que podem ser produzidas e quaisquer limites de dimensionamento ou outros requisitos.

### Todos os tipos de modelo

<table summary="Esta tabela fornece um resumo de entrada, saída e limitações para todos os tipos de modelo.">
  <caption>Tabela 1. Todos os tipos de modelo</caption>
  <tr>
    <th style="vertical-align:bottom; text-align:left" id="d25459e252">
      Tarefa
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e254">
      Uso típico
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e256">
      Formatos de entrada suportados
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e258">
      Formatos de saída suportados
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e260">
      Limites e requisitos
    </th>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e252">
      <p>Gerenciamento de sistema de tipos</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e254">
      <p>Crie um sistema de tipos ou faça upload e modifique um sistema de tipos existente.</p>
      <p>Defina tipos de entidade
e tipos de relação para seu domínio.</p>
      <p>Não é possível ver uma visualização do sistema
de tipos.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e256">
      <ul>
        <li>
          <p>Arquivo JSON transferido por download de uma área de trabalho do {{site.data.keyword.knowledgestudioshort}}</p>
        </li>
        <li>
          <p>Arquivo ZIP que você transferiu por download do Human Annotation Tool (HAT)</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e258">
      <ul>
        <li>
          <p>JSON</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e260">
      <p>Para evitar a sobrecarga visual para anotação humana, defina não mais que 50 tipos de entidade e 50
tipos de relação.</p>
      <p>Limitação de tamanho do arquivo para fazer upload de um sistema de tipos: 20 MB</p>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e252">
      <p>Gerenciamento de dicionário</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e254">
      <p>Faça upload de um arquivo de dicionário CSV no modo somente leitura ou um ZIP de dicionários que você transferiu por download
de outra área de trabalho.</p>
      <p>Crie um novo dicionário e, em seguida, faça upload de um arquivo CSV de entradas de termos ou inclua
entradas de termos nele.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e256">
      <p>Arquivo de dicionário:</p>
      <ul>
        <li>
          <p>Arquivo CSV em formato UTF-8</p>
        </li>
        <li>
          <p>ZIP de dicionários transferidos por download de outra área de trabalho</p>
        </li>
      </ul>
      <p>Arquivo de entradas de termos:</p>
      <ul>
        <li>
          <p>Arquivo CSV em formato UTF-8</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e258">
      <ul>
        <li>
          <p>Arquivo CSV em formato UTF-8</p>
        </li>
        <li>
          <p>ZIP de dicionários para uso em outra área de trabalho</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e260">
      <p>Limitações de tamanho do arquivo:</p>
      <ul>
        <li>
          <p>1 MB por arquivo CSV de entradas de termos</p>
        </li>
        <li>
          <p>16 MB por arquivo CSV de dicionário somente leitura</p>
        </li>
        <li>
          <p>15.000 entradas por dicionário, exceto um dicionário somente leitura</p>
        </li>
        <li>
          <p>64 dicionários por área de trabalho</p>
        </li>
      </ul>
    </td>
  </tr>
</table>

 {: #wks_formats__datasimpletable_xxj_qr5_2y}

### Modelo de aprendizado de máquina

<table summary="Esta tabela fornece um resumo de entrada, saída e limitações para o modelo de aprendizado de máquina.">
  <caption>Tabela 2. Modelo de aprendizado de</caption>
  <tr>
    <th style="vertical-align:botton; text-align:left" id="d25459e331">Tarefa</th>
    <th style="vertical-align:botton; text-align:left" id="d25459e333">Uso típico</th>
    <th style="vertical-align:botton; text-align:left" id="d25459e335">Formatos de entrada suportados</th>
    <th style="vertical-align:botton; text-align:left" id="d25459e337">Formatos de saída suportados</th>
    <th style="vertical-align:botton; text-align:left" id="d25459e339">Limites e requisitos</th>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>Gerenciamento de documentos </p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
      <p>Faça upload de um pequeno subconjunto, representante de documentos</p>
      <p>Faça upload de documentos que contêm
anotações incluídas anteriormente por um anotador humano, um modelo de aprendizado de máquina ou um
mecanismo de análise
UIMA</p>
      <p>Não é possível alimentar o corpus inteiro do {{site.data.keyword.ibmwatson_notm}} Explorer para calcular documentos de valor alto para anotação.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <ul>
        <li>
          <p>Arquivo CSV em formato UTF-8</p>
        </li>
        <li>
          <p>Texto no formato UTF-8</p>
        </li>
        <li>
          <p>Arquivo ZIP que contém documentos transferidos por download de outro corpus</p>
        </li>
        <li>
          <p>Arquivo ZIP que contém documentos em
formato
XMI do UIMA CAS</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <ul>
        <li>
          <p>Archive ZIP de documentos</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <ul>
        <li>
          <p>40.000 caracteres por documento</p>
        </li>
        <li>
          <p>10.000 documentos por área de trabalho</p>
        </li>
        <li>
          <p>1.000 conjuntos de documentos (incluindo conjuntos de anotações) por área de trabalho</p>
        </li>
      </ul>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>Pré-anotação</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
       <p>Use um dicionário ou
pré-anotador do {{site.data.keyword.nlufull}}
para fornecer
um ponto de início para anotação humana.</p>
       <p>Não é possível anotar novamente um corpus do {{site.data.keyword.ibmwatson_notm}} Explorer.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <p>Documentos brutos.</p>
      <p><b>Nota:</b> não pré-anote os documentos que um anotador humano já
anotou ou você perderá o trabalho feito pelo anotador humano.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <p>Documentos parcialmente anotados</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <p>Nenhuma</p>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>Anotação de documento</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
      <p>Gerenciar anotação humana</p><p>Anote as entidades, as relações e cadeias de correferência para criar
verdade absoluta</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <p>Tarefa de anotação</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <p>Verdade absoluta</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <ul>
        <li>
          <p>256 tarefas de anotação ativas por área de trabalho</p>
        </li>
      </ul>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>Treinamento e refinamento</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
      <p>Treine um modelo de aprendizado de máquina supervisionado para extrair informações específicas do domínio do
texto não estruturado.</p><p>Avalie e melhore um modelo de aprendizado de máquina supervisionado.</p>
      <p>Não é possível
criar um modelo de aprendizado de máquina semisupervisionado ou não supervisionado.</p>
      <p>Não é possível
fazer engenharia de recurso extensivo.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <p>Não aplicável</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <p>Modelo de aprendizado de máquina</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <ul>
        <li>
          <p>1 modelo de aprendizado de máquina por área de trabalho</p>
        </li>
        <li>
          <p>10 versões de modelo por área de trabalho</p>
        </li>
        <li>
          <p>O número máximo de áreas de trabalho é determinado por seu plano de assinatura.</p>
        </li>
        <li>
          <p>O número máximo de ações de treinamento que é possível executar por mês é determinado por seu plano de assinatura.</p>
        </li>
      </ul>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e331">
      <p>Publicação</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e333">
      <p>Publique um modelo de aprendizado de máquina a ser usado para executar a extração de texto em outros aplicativos do {{site.data.keyword.watson}}.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e335">
      <p>Não aplicável</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e337">
      <ul>
        <li>
          <p>ID de modelo (para uso no {{site.data.keyword.nlufull}} ou no {{site.data.keyword.discoveryfull}})</p>
        </li>
        <li>
          <p>Arquivo ZIP (para uso no  {{site.data.keyword.ibmwatson_notm}}  Explorer)</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e339">
      <p>Para implementar em serviços {{site.data.keyword.watson}}, o espaço de serviço do {{site.data.keyword.cloud_notm}} e os nomes de instâncias devem ser conhecidos.</p>
    </td>
  </tr>
</table>

### Modelo baseado em regra

<table summary="Esta tabela fornece um resumo de entrada, saída e limitações para o modelo baseado em regra.">
  <caption>Tabela 3. Modelo baseado em regra</caption>
  <tr>
    <th style="vertical-align:bottom; text-align:left" id="d25459e509">
      Tarefa
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e511">
      Uso típico
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e513">
      Formatos de entrada suportados
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e515">
      Formatos de saída suportados
    </th>
    <th style="vertical-align:bottom; text-align:left" id="d25459e517">
      Limites e requisitos
    </th>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e509">
      <p>Editor de regras</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e511">
      <p>Crie ou faça upload de documentos para o editor de regras por meio do qual as classes, expressões regulares e regras são definidas.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e513">
      <ul>
        <li>
          <p>Texto simples (incluído no editor)</p>
        </li>
        <li>
          <p>Arquivo CSV em formato UTF-8</p>
        </li>
        <li>
          <p>Copiado do conjunto de documentos Todos</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e515">
      <p>Nenhuma</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e517">
      <ul>
        <li>
          <p>1 modelo baseado em regra por área de trabalho</p>
        </li>
        <li>
          <p>5.000 caracteres por documento</p>
        </li>
        <li>
          <p>100 documentos por área de trabalho</p>
        </li>
        <li>
          <p>O tamanho máximo de título do documento é 256 caracteres</p>
        </li>
        <li>
          <p>200 regras por área de trabalho</p>
        </li>
        <li>
          <p>400 classes por área de trabalho</p>
        </li>
        <li>
          <p>Grupo de 100 expressões regulares por área de trabalho</p>
        </li>
        <li>
          <p>100 entradas de expressão regular por grupo de expressões regulares</p>
        </li>
        <li>
          <p>1.000 caracteres por entrada de expressão regular</p>
        </li>
        <li>
          <p>5 versões de modelo baseado em regra por área de trabalho</p>
        </li>
      </ul>
    </td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:left" headers="d25459e509">
      <p>Publicação</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e511">
      <p>Publique um modelo baseado em regra a ser usado para executar reconhecimento de padrão em outros aplicativos do {{site.data.keyword.watson}}.</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e513">
      <p>Não aplicável</p>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e515">
      <ul>
        <li>
          <p>ID de modelo (para uso no {{site.data.keyword.nlufull}} ou no {{site.data.keyword.discoveryfull}})</p>
        </li>
      </ul>
    </td>
    <td style="vertical-align:top; text-align:left" headers="d25459e517">
      <p>Para implementar em serviços {{site.data.keyword.watson}}, o espaço de serviço do {{site.data.keyword.cloud_notm}} e os nomes de instâncias devem ser conhecidos.</p>
    </td>
  </tr>
</table>
