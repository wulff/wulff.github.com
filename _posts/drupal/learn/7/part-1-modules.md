# Installér moduler

% ============================================================================
\chapter{Moduler}
\chapterprecis{Fortæller dig hvordan du installerer tredjepartsmoduler og giver en gennemgang af de vigtigste moduler.}

\noindent
Kernen af Drupal består af omkring 50 moduler, hvoraf kun de 7 er obligatoriske. Som du kan se i \ref{part-tutorial}, \emph{Dit første Drupal-site}, kan man komme langt ved blot at bruge en fornuftig kombination af de indbyggede moduler.

Her giver vi dig et overblik over alle de moduler, som er en del af Drupal~7, og giver dig derefter en vejledning til hvordan du finder og installerer nyttige tredjepartsmoduler (også kaldet \emph{contrib}-moduler).

% ----------------------------------------------------------------------------
\section{Indbyggede moduler} \label{section-modules-core}

Dette afsnit indeholder beskrivelser af alle de moduler, som følger med i en standard Drupal~7-installation. I de tilfælde hvor tredjepartsmoduler tilbyder bedre eller mere fleksible løsninger er det nævnt i beskrivelsen.

\subsection{Obligatoriske moduler}

Disse moduler udgør den absolutte kerne af Drupal, og de er derfor aktiveret på alle Drupal-sites.

\begin{description}
\item[Field] Tilføjer brugerdefinerede felter til noder, brugerprofiler, taksonomitermer og andre entiteter. Felter kan indeholder tekst, tal, links, e-mail-adresser, billeder og meget andet afhængigt af hvilke feltmoduler du har installeret.
\item[Field SQL storage] Gemmer indholdet af de brugerdefinerede felter i en SQL-database. Dette er pt.\ den eneste mulighed, men på sigt kan der blive tilføjet flere lagringsmuligheder.
\item[Filter] Tilbyder forskellige indholdsfiltre, som f.eks. omdannelse af URLer til klikbare links og sikring mod uønskede HTML-tags.
\item[Node] Håndterer alt indholdet på sitet.
\item[System] Håndterer grundlæggende funktioner som f.eks. sitets indstillinger, udsendelse af mail samt opdatering af moduler og temaer.
\item[Text] Definerer forskellige typer af tekstfelter til brug med \emph{Field}-modulet.
\item[User] Håndterer brugerprofiler og tilladelser.
\end{description}

\subsection{Moduler i installationsprofilen \emph{Minimal}}

Hvis du vælger at installere Drupal fra installationsprofilen \emph{Minimal} aktiveres følgende moduler udover de obligatoriske moduler.

\begin{description}
\item[Block] Viser blokke med indhold i forskellige regioner på dit site. Blokke kan f.eks. indeholde søgefelter, lister af populært indhold m.m.
\item[Database logging] Skriver fejlmeddelelser og anden driftsinformation til en tabel i databasen.
\item[Update manager] Søger efter tilgængelige opdateringer og kan installere eller opdatere moduler og temaer. Hvis der er opdateringer til et eller flere af dine installerede moduler eller temaer sender \emph{Update manager} en e-mail til den adresse, som er angivet på \emph{Reports $\rightarrow$ Available updates $\rightarrow$ Settings}. På samme side kan du vælge om søgningen skal foretages dagligt eller ugentligt.
\end{description}

\subsection{Moduler i installationsprofilen \emph{Standard}}

Hvis du installerer Drupal fra installationsprofilen \emph{Standard} aktiveres følgende moduler udover modulerne fra \emph{Minimal} og de obligatoriske moduler.

\begin{itemize}
\item Color
\item Comment
\item Contextual links
\item Dashboard
\item Field UI
\item File
\item Help
\item Image
\item List
\item Menu
\item Number
\item Options
\item Overlay
\item Path
\item RDF
\item Search
\item Shortcut
\item Taxonomy
\item Toolbar
\end{itemize}

\subsection{Valgfri moduler}

De resterende moduler bliver ikke aktiveret af de indbyggede installationsprofiler, men er til rådighed hvis du får brug for dem.

\begin{description}
\item[Aggregator] Brug Feeds i stedet
\item[Blog]
\item[Book]
\item[Contact]
\item[Content translation]
\item[Forum] Advanced forum
\item[Locale] Gør det muligt at oversætte Drupals grænseflade til andre sprog end engelsk (modulet aktiveres kun hvis du vælger at installere Drupal på et andet sprog end engelsk).
\item[OpenID]
\item[PHP filter]
\item[Poll]
\item[Statistics]
\item[Syslog]
\item[Testing]
\item[Tracker]
\item[Trigger]
\end{description}

% ----------------------------------------------------------------------------
\section{Installation af moduler}

\begin{itemize}
\item manuel installation
\item automatisk installation
\item drupalmodules.com
\end{itemize}

% ----------------------------------------------------------------------------
\section{Tredjepartsmoduler}

% TODO: beskriv de moduler, som ingen kan leve uden. ...se desuden appendix C.
% TODO: hvor finder man dem: drupal.org, drupalmodules.com, drupaldanmark.dk
