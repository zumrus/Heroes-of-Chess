# Heroes of Chess: Game Rules

Heroes of Chess is a chess variant inspired by the combat system of the classic strategy game Heroes of Might and Magic III.

The game is played on a standard chessboard with the usual starting setup. Pieces move exactly as they do in regular chess, but the goal is not to check or checkmate the opponent, but to destroy the enemy king and all pawns that are capable of turning into a new one.

## Key Differences from Standard Chess

- The king is a full participant in combat and the most powerful piece on the board.
- During one turn, all pieces get to act; the order depends on piece rank and on the use of the tactical option "Wait".
- When one piece attacks another, the defender loses hit points determined by piece rank. A piece leaves the board only when its hit points drop to zero. Initial health depends on rank, and the damage a piece deals depends on the difference in ranks.

## Basic Principles and Piece Ranks

Rank in Heroes of Chess differs slightly from rank in traditional chess.

| Piece | Rank (stats) |
|---|---:|
| Pawn | 1 |
| Knight | 2 |
| Bishop | 3 |
| Rook | 5 |
| Queen | 7 |
| King | 9 |

Rank determines all of a piece's characteristics:

- Turn order: kings move first, pawns move last. If a player has several identical pieces, such as pawns, they alternate turns: first the white pawn, then the black pawn, then white again, and so on. Counting goes by files, starting from the leftmost pieces.
- Initial number of hit points.
- Damage dealt by the piece. It is calculated as the difference between the attacker's and defender's ranks, but it can never be less than 1. When calculating damage, the defender's rank may be increased by 1 if the "Defense" command is used.

## What Can You Do on Your Turn?

When it is your piece's turn to act, you have three options:

1. **Action** (move / attack)

   You may move a piece to an empty square according to normal chess rules. A piece may attack another piece if that target stands on a square adjacent to a square your piece could move to, and only in a direction that the piece is allowed to move in. For example, a bishop cannot move or attack vertically or horizontally, while a rook cannot move or attack diagonally.

   In this case, the attacking piece moves to the square from which the attack is made, rather than occupying the target's square if the target is removed from the board. The exception is the knight: it attacks at range, but only within the standard chess "L-shaped" pattern.

2. **Defend** (shield button)

   If you do not want to move anywhere, or cannot, the piece stays in place and enters full defense. For damage calculation, its rank is increased by 1 until the end of the current turn.

3. **Wait** (hourglass button)

   The piece skips its action for now, but must act at the very end of the turn. This option can be used only once per turn. On the first turn, for convenience, all pieces of rank 3 and higher are automatically set to Wait, since they are blocked by pawns.

Each turn is divided into two phases: the normal phase, where order is determined by the rules above, and the waiting phase, where the order is reversed. As a result, the higher the rank of a piece, the more prolonged its tactical maneuver within the turn.

## Other Features

**Counterattack.** A piece that survives an attack immediately strikes back using the same rules. Regular pieces may counterattack only once per turn. The king is the exception: it always counterattacks every attack against it.

**Death of the King and Saving Pawns.** If your king is killed, the game does not end immediately, but the following happens:

- You lose control of your army. In the computer version, your remaining pieces enter "Berserk" mode and move according to the berserk bot algorithm described below. 
- If your berserk pawn reaches the opposite edge of the board, it automatically turns into a new king, and you regain full control of the game.
- If the king is dead and there are no pawns left on the board, this is a final defeat.

## Berserk Bot Algorithm

To make solo play possible, I developed a simple algorithm for the computer opponent. Berserk pieces always attack if they can. If there are multiple possible targets, they choose the strongest one by main rank. If there is still more than one such target, the chosen one is the piece with the lowest vertical and horizontal coordinates.

Pieces that cannot attack move randomly around the board within the limits of legal movement. The exception is pawns, which always move forward.

The berserk bot does not use Wait or Defense. The only exception is when a piece can neither attack nor move because it is blocked by other pieces.

## Playing Without a Computer


- The game can be played using a regular chessboard.
- For high-rank pieces, it is enough to keep small notes on their health points.
- The “Wait” command can be indicated by slightly shifting the piece backward within its square.
- The “Defend” command can be indicated by slightly shifting the piece forward within its square.
- The berserk algorithm is difficult to use directly in the tabletop version because it relies on a random move generator, but before the game begins, the players can agree on their own simpler algorithm — for example, non-attacking pieces move only forward and to the left, then backward and to the right.