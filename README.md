class Solution:
    def findUnion(self, a, b):
        i, j = 0, 0
        res = []
        
        # Helper function to avoid adding duplicates
        def append_if_unique(val):
            if not res or res[-1] != val:
                res.append(val)

        # Iterate through both arrays
        while i < len(a) and j < len(b): # Fixed: len(b) instead of len(j)
            if a[i] < b[j]:
                append_if_unique(a[i])
                i += 1
            elif b[j] < a[i]:
                append_if_unique(b[j])
                j += 1
            else:
                # Both are equal, add once and move both
                append_if_unique(a[i])
                i += 1
                j += 1
        
        # Add remaining elements from array a
        while i < len(a):
            append_if_unique(a[i])
            i += 1
            
        # Add remaining elements from array b
        while j < len(b):
            append_if_unique(b[j])
            j += 1
            
        return res
