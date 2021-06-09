# Marketing-Cells-task

package marking.cells;

public class MarkingCells {
 
    public static void checked(
        int matrix[][], int n)
    { //boolean to know if it is done visited or not
        boolean done[][] = new boolean[n][n];
        boolean flag = false;
 //to check the matrix 
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                if (matrix[i][j] == 1   && !done[i][j])
                    if (checked(  matrix, i, j, done))
                     { flag = true;
                        break;}
            }
        }
        if (flag)
            System.out.println("YES");
        else
            System.out.println("NO");
    }
 
    public static boolean path(
        int i, int j,
        int matrix[][])
    {
        if ( i >= 0 && i < matrix.length && j >= 0 && j < matrix[0].length)
        return true;
        return false;
    }
    //Returns true if there is a path from a starting pointto an end point
 
    public static boolean checked(
        int matrix[][],
        int i, int j,
        boolean done[][])
    {
 
        if (
            path(i, j, matrix)
            && matrix[i][j] != 0
            && !done[i][j]) {
            done[i][j] = true;
 
            if (matrix[i][j] == 2)
                return true;
 //traverse up
            boolean up = checked( matrix, i - 1,     j, done);
            if (up)
             return true;
 //traverse down
            boolean down = checked( matrix, i + 1, j, done);
            if (down)
                return true;
 
 //traverse right
            boolean right= checked(matrix, i, j + 1,  done);
            if (right)
                return true;
 //traverse left
            boolean left = checked(  matrix, i, j - 1, done);
            if (left)
                return true;
        }
        return false;
    }
    
    public static void main(String[] args) {
        
       {
 
        int matrix[][] = { { 0, 3, 0, 1 },
                           { 3, 0, 3, 3 },
                           { 2, 3, 3, 3 },
                           { 0, 3, 3, 3 } };
 
        // calling isPath method
        checked(matrix, 4);
    }
    }
    
}
